# Azure AI Foundry Quick Reference

## Quick Start Checklist

- [ ] Create Azure subscription (or use existing)
- [ ] Access Azure AI Foundry portal: https://ai.azure.com
- [ ] Create an Azure AI Foundry project
- [ ] Deploy a model (e.g., GPT-4o)
- [ ] Test in playground
- [ ] Get project endpoints and keys
- [ ] Build your first application

## Essential URLs

| Resource | URL |
|----------|-----|
| Azure AI Foundry Portal | https://ai.azure.com |
| Azure Portal | https://portal.azure.com |
| Microsoft Learn | https://learn.microsoft.com/training/paths/create-custom-copilots-ai-studio/ |
| Exercise Repository | https://github.com/MicrosoftLearning/mslearn-ai-studio |
| Exercise Website | https://go.microsoft.com/fwlink/?linkid=2310724 |

## Key Concepts at a Glance

### Azure AI Foundry Resource
- Central hub for AI development
- Manages connections to AI services
- Provides access control and governance
- Best for individual developers and small teams

### AI Hub Resource
- Enterprise-grade resource management
- Secure storage and compute
- Specialized tools and capabilities
- Best for large teams and complex solutions

### Project
- Collaborative workspace
- Contains models, data, and endpoints
- Isolated environment for development
- Can be created within Foundry or Hub resources

## Common CLI Commands

### Azure CLI Setup
```bash
# Login to Azure
az login

# Set subscription
az account set --subscription "YOUR_SUBSCRIPTION_ID"

# Install AI extension
az extension add --name ml
```

### Resource Management
```bash
# List resource groups
az group list --output table

# Create resource group
az group create --name "rg-ai-foundry" --location "eastus"

# Delete resource group (cleanup)
az group delete --name "rg-ai-foundry" --yes --no-wait
```

## Python SDK Quick Start

### Installation
```bash
pip install azure-ai-projects
pip install azure-identity
pip install openai
```

### Basic Connection
```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

# Connect to project
project = AIProjectClient.from_connection_string(
    conn_str="YOUR_CONNECTION_STRING",
    credential=DefaultAzureCredential()
)
```

### Chat Completion
```python
from openai import AzureOpenAI

client = AzureOpenAI(
    api_key="YOUR_API_KEY",
    api_version="2024-02-15-preview",
    azure_endpoint="YOUR_ENDPOINT"
)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is Azure AI Foundry?"}
    ]
)

print(response.choices[0].message.content)
```

### RAG Implementation Pattern
```python
# Simplified RAG pattern
def rag_query(user_question, knowledge_base):
    # 1. Retrieve relevant context
    relevant_docs = search_knowledge_base(user_question, knowledge_base)
    
    # 2. Build prompt with context
    context = "\n".join(relevant_docs)
    prompt = f"""Answer the question based on the following context:
    
Context:
{context}

Question: {user_question}

Answer:"""
    
    # 3. Get AI response
    response = client.chat.completions.create(
        model="gpt-4o",
        messages=[
            {"role": "system", "content": "You are a helpful assistant. Only answer based on the provided context."},
            {"role": "user", "content": prompt}
        ]
    )
    
    return response.choices[0].message.content
```

## Model Comparison

| Model | Best For | Context Window | Speed | Cost |
|-------|----------|----------------|-------|------|
| GPT-4o | Complex reasoning, coding | 128K tokens | Medium | High |
| GPT-4o-mini | Cost-effective tasks | 128K tokens | Fast | Low |
| GPT-3.5-turbo | Simple tasks, chat | 16K tokens | Very Fast | Very Low |

## Token Management

### Estimation Rules of Thumb
- 1 token ≈ 4 characters
- 1 token ≈ 0.75 words
- 100 tokens ≈ 75 words

### Token Limits
- **TPM (Tokens Per Minute)**: Rate limit for API calls
- **Context Window**: Maximum tokens in a single request
- **Output Tokens**: Maximum tokens in response

### Cost Optimization
```python
# Count tokens before sending
from tiktoken import encoding_for_model

encoder = encoding_for_model("gpt-4o")
token_count = len(encoder.encode(your_text))
```

## Prompt Engineering Patterns

### System Message Best Practices
```python
# Good: Clear role and constraints
system_message = """You are a customer support agent for a software company.
Rules:
- Be professional and friendly
- Provide accurate information
- If unsure, say so and offer to escalate
- Keep responses concise (under 100 words)
"""

# Bad: Vague instructions
system_message = "Help the user"
```

### Few-Shot Learning
```python
messages = [
    {"role": "system", "content": "Convert product names to SKUs."},
    {"role": "user", "content": "Pro Laptop 15"},
    {"role": "assistant", "content": "SKU: PL15-001"},
    {"role": "user", "content": "Basic Mouse Wireless"},
    {"role": "assistant", "content": "SKU: BMW-002"},
    {"role": "user", "content": "Premium Keyboard RGB"}
]
```

### Chain of Thought
```python
prompt = """Let's solve this step by step:
1. First, identify the key information
2. Then, analyze the requirements
3. Finally, provide the solution

Question: {user_question}
"""
```

## Content Filter Configuration

### Severity Levels
- **Safe**: No filtering
- **Low**: Minimal filtering
- **Medium**: Balanced (recommended for most apps)
- **High**: Strict filtering

### Filter Categories
1. **Hate**: Discriminatory content
2. **Sexual**: Adult content
3. **Violence**: Harmful content
4. **Self-Harm**: Dangerous behaviors

### Custom Filters
```python
# Example configuration
content_filter_config = {
    "hate": {"severity": "medium"},
    "sexual": {"severity": "high"},
    "violence": {"severity": "medium"},
    "self_harm": {"severity": "high"}
}
```

## Error Handling

### Common HTTP Status Codes
- **200**: Success
- **400**: Bad request (check parameters)
- **401**: Unauthorized (check API key)
- **429**: Rate limit exceeded (implement retry)
- **500**: Server error (retry with backoff)

### Retry Pattern
```python
import time
from openai import RateLimitError

def call_with_retry(func, max_retries=3):
    for attempt in range(max_retries):
        try:
            return func()
        except RateLimitError as e:
            if attempt == max_retries - 1:
                raise
            wait_time = 2 ** attempt  # Exponential backoff
            print(f"Rate limited. Waiting {wait_time}s...")
            time.sleep(wait_time)
```

## Evaluation Metrics

### Quality Metrics
- **Groundedness**: Responses based on provided context
- **Relevance**: Answers address the question
- **Coherence**: Logical and well-structured
- **Fluency**: Natural language quality

### Example Evaluation
```python
# Simplified evaluation function
def evaluate_response(question, context, response):
    eval_prompt = f"""Evaluate this AI response:
    
Question: {question}
Context: {context}
Response: {response}

Rate each metric (0-5):
- Groundedness (uses only provided context)
- Relevance (answers the question)
- Coherence (logical and clear)
- Fluency (natural language)

Provide scores as JSON."""

    # Use another model call for evaluation
    eval_result = client.chat.completions.create(...)
    return eval_result
```

## Deployment Patterns

### Azure App Service
```bash
# Deploy Python app
az webapp up --name my-ai-app --runtime "PYTHON:3.11"
```

### Azure Functions
```python
# function_app.py
import azure.functions as func
from openai import AzureOpenAI

app = func.FunctionApp()

@app.route(route="chat", methods=["POST"])
def chat_function(req: func.HttpRequest) -> func.HttpResponse:
    message = req.get_json().get('message')
    # Call AI model
    response = get_ai_response(message)
    return func.HttpResponse(response)
```

### Container Apps
```dockerfile
# Dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

## Security Best Practices

### API Key Management
```python
# Use environment variables
import os
from azure.identity import DefaultAzureCredential

# Never hardcode keys
api_key = os.environ.get("AZURE_OPENAI_KEY")

# Better: Use managed identity
credential = DefaultAzureCredential()
```

### Rate Limiting Client-Side
```python
from collections import deque
from time import time

class RateLimiter:
    def __init__(self, max_calls_per_minute):
        self.max_calls = max_calls_per_minute
        self.calls = deque()
    
    def wait_if_needed(self):
        now = time()
        # Remove calls older than 1 minute
        while self.calls and self.calls[0] < now - 60:
            self.calls.popleft()
        
        if len(self.calls) >= self.max_calls:
            sleep_time = 60 - (now - self.calls[0])
            time.sleep(sleep_time)
        
        self.calls.append(time())
```

## Monitoring and Logging

### Basic Logging
```python
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def call_ai_model(prompt):
    logger.info(f"Calling model with prompt length: {len(prompt)}")
    try:
        response = client.chat.completions.create(...)
        logger.info(f"Response received: {len(response)} tokens")
        return response
    except Exception as e:
        logger.error(f"Error calling model: {e}")
        raise
```

### Azure Application Insights
```python
from opencensus.ext.azure.log_exporter import AzureLogHandler

logger.addHandler(AzureLogHandler(
    connection_string='InstrumentationKey=YOUR_KEY'
))
```

## Testing Strategies

### Unit Tests
```python
import unittest
from unittest.mock import Mock, patch

class TestAIIntegration(unittest.TestCase):
    @patch('openai.AzureOpenAI')
    def test_chat_completion(self, mock_client):
        # Mock the API response
        mock_client.chat.completions.create.return_value = Mock(
            choices=[Mock(message=Mock(content="Test response"))]
        )
        
        # Test your function
        result = your_chat_function("Test question")
        self.assertEqual(result, "Test response")
```

### Integration Tests
```python
def test_end_to_end():
    """Test actual API call (use separate test environment)"""
    response = client.chat.completions.create(
        model="gpt-4o",
        messages=[{"role": "user", "content": "Say 'test passed'"}]
    )
    assert "test passed" in response.choices[0].message.content.lower()
```

## Troubleshooting Checklist

### Connection Issues
- [ ] Verify API endpoint URL
- [ ] Check API key is correct
- [ ] Confirm API version is supported
- [ ] Check firewall/network settings

### Performance Issues
- [ ] Monitor token usage
- [ ] Check TPM limits
- [ ] Optimize prompt length
- [ ] Review system message complexity
- [ ] Consider response caching

### Quality Issues
- [ ] Review system message clarity
- [ ] Add more context or examples
- [ ] Adjust temperature parameter
- [ ] Test with different prompts
- [ ] Implement evaluation metrics

### Cost Issues
- [ ] Monitor token consumption
- [ ] Set TPM limits appropriately
- [ ] Cache common responses
- [ ] Use appropriate model tier
- [ ] Implement request filtering

## Useful Resources

### Documentation
- [Azure AI Foundry Docs](https://learn.microsoft.com/azure/ai-studio/)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)
- [Prompt Engineering Guide](https://learn.microsoft.com/azure/ai-services/openai/concepts/prompt-engineering)

### Tools
- [Azure SDK for Python](https://github.com/Azure/azure-sdk-for-python)
- [OpenAI Python Client](https://github.com/openai/openai-python)
- [Tiktoken](https://github.com/openai/tiktoken) - Token counting

### Community
- [Azure AI Discord](https://discord.gg/azure-ai)
- [Microsoft Tech Community](https://techcommunity.microsoft.com/t5/ai-azure-ai-services/ct-p/Azure-AI-Services)
- [Stack Overflow - Azure AI](https://stackoverflow.com/questions/tagged/azure-ai)

---

**Note**: This is a quick reference guide. For detailed information, see the [Complete Study Guide](./STUDY_GUIDE.md).
