# Azure AI Foundry Study Guide

## Overview

This study guide provides a comprehensive overview of the Microsoft Learn Azure AI Studio (now Azure AI Foundry) learning repository. The repository offers hands-on exercises for developing generative AI solutions on Microsoft Azure.

**Repository:** [MicrosoftLearning/mslearn-ai-studio](https://github.com/MicrosoftLearning/mslearn-ai-studio)

## Prerequisites

- **Azure Subscription**: Required with sufficient permissions and quota to provision Azure resources and generative AI models
- **Azure Account**: Free trial available for new users with credits for the first 30 days
- **Basic Understanding**: Familiarity with cloud computing concepts and AI/ML basics

## Course Structure

The repository contains 7 main exercises plus additional supplementary content, designed to provide hands-on experience with common developer tasks when building generative AI solutions.

### Exercise 1: Prepare for an AI Development Project
**Duration:** ~30 minutes  
**Focus:** Azure AI Foundry portal setup and project management

**Key Learning Objectives:**
- Navigate Azure AI Foundry portal
- Create and configure AI projects
- Understand Azure AI Foundry resources vs AI Hub resources
- Deploy and configure GPT-4o model
- Set token per minute (TPM) rate limits
- Explore project endpoints and authorization keys
- Test generative AI models in the chat playground

**Key Concepts:**
- **Azure AI Projects**: Collaborative workspaces for AI development
- **Azure AI Foundry Resources**: Provide access to AI models (including Azure OpenAI), Azure AI services, and development resources
- **AI Hub Resources**: Enterprise-grade resources for complex AI solutions with secure storage, compute, and specialized tools
- **Model Deployment**: Using Global standard deployment types with customizable TPM limits
- **Endpoints**: Connection points for client applications to access projects and models

### Exercise 2: Explore Model Catalog
**Focus:** Understanding and exploring available AI models

**Key Learning Objectives:**
- Browse the Azure AI model catalog
- Understand different model types and capabilities
- Compare model features and performance characteristics
- Select appropriate models for specific use cases

### Exercise 2a: AI Foundry SDK
**Focus:** Programmatic access to Azure AI Foundry capabilities

**Key Learning Objectives:**
- Use Azure AI Foundry SDK for Python
- Authenticate and connect to projects programmatically
- Deploy and manage models via code
- Integrate AI capabilities into applications

### Exercise 3: Use Prompt Flow for Chat Applications
**Focus:** Building conversational AI applications

**Key Learning Objectives:**
- Understand prompt flow architecture
- Design and implement chat flows
- Test and debug conversational AI
- Deploy chat applications

### Exercise 4: Use Your Own Data (RAG - Retrieval Augmented Generation)
**Focus:** Integrating custom data sources with AI models

**Key Learning Objectives:**
- Implement Retrieval Augmented Generation (RAG)
- Index and search custom data
- Ground model responses in enterprise data
- Build knowledge-based chat applications

**Key Concepts:**
- **RAG Pattern**: Technique to provide AI models with relevant context from custom data sources
- **Data Indexing**: Preparing and organizing data for efficient retrieval
- **Grounding**: Ensuring model responses are based on factual, domain-specific information

### Exercise 5: Fine-tune Models
**Focus:** Customizing models for specific tasks and domains

**Key Learning Objectives:**
- Understand when to fine-tune vs use RAG
- Prepare training data for fine-tuning
- Execute fine-tuning jobs
- Evaluate fine-tuned model performance
- Deploy custom models

### Exercise 6: Explore Content Filters
**Focus:** Responsible AI and content safety

**Key Learning Objectives:**
- Implement content safety measures
- Configure content filters for inputs and outputs
- Test harmful content detection
- Apply responsible AI principles

**Key Concepts:**
- **Content Safety**: Preventing harmful, offensive, or inappropriate content
- **Input Filters**: Screening user prompts before processing
- **Output Filters**: Reviewing model responses before delivery
- **Responsible AI**: Ethical considerations in AI deployment

### Exercise 7: Evaluate Prompt Flow
**Focus:** Quality assurance and performance evaluation

**Key Learning Objectives:**
- Define evaluation metrics
- Create test datasets
- Run automated evaluations
- Analyze and improve model performance

## Key Technologies and Tools

### Azure AI Foundry Portal
- Web-based interface for managing AI projects
- Integrated playground for testing models
- Project and resource management capabilities
- Model deployment and configuration tools

### Azure OpenAI Service
- Access to GPT-4o and other OpenAI models
- API endpoints for programmatic access
- Token management and rate limiting
- Fine-tuning capabilities

### Prompt Flow
- Visual designer for AI workflows
- Testing and debugging tools
- Deployment automation
- Integration with Azure services

### Azure AI Services
- Cognitive services integration
- Content safety and moderation
- Speech, vision, and language capabilities
- Custom model training

## Lab Files Structure

The repository includes practical code samples and resources:

### Chat App (`labfiles/chat-app/`)
- Basic chat application implementation
- Frontend and backend code examples
- Integration patterns with Azure OpenAI

### RAG App (`labfiles/rag-app/`)
- Retrieval Augmented Generation implementation
- Data indexing and search examples
- Custom knowledge base integration

### Data Files (`data/` and `text-files/`)
- Sample datasets for exercises
- Training data examples
- Test data for evaluations

## Best Practices

### Project Organization
1. **Use descriptive naming**: Name projects clearly to reflect their purpose
2. **Manage resources**: Clean up unused resources to avoid unnecessary costs
3. **Set appropriate quotas**: Configure TPM limits based on expected usage
4. **Use resource groups**: Organize related resources for easier management

### Model Deployment
1. **Start with recommended regions**: Use AI Foundry recommended regions for better model availability
2. **Monitor token usage**: Track TPM consumption to avoid quota limits
3. **Test thoroughly**: Use playgrounds before production deployment
4. **Implement fallbacks**: Handle rate limiting and errors gracefully

### Security and Compliance
1. **Implement content filters**: Always use content safety measures
2. **Manage access**: Use role-based access control (RBAC) appropriately
3. **Secure endpoints**: Protect API keys and endpoints
4. **Audit usage**: Monitor and log AI service usage

### Development Workflow
1. **Prototype in playground**: Test prompts and configurations quickly
2. **Use version control**: Track prompt and configuration changes
3. **Automate testing**: Create evaluation datasets for consistent testing
4. **Iterate incrementally**: Make small changes and test frequently

## Cost Management

### Strategies to Minimize Costs
- Delete resources after completing exercises
- Use appropriate TPM rate limits
- Leverage free tier credits when available
- Monitor usage through Azure Cost Management
- Use resource groups for bulk deletion

### Resource Cleanup
Always delete resource groups when finished with exercises to avoid ongoing charges:
1. Navigate to Azure Portal
2. Select the resource group
3. Click "Delete resource group"
4. Confirm by entering the resource group name

## Common Patterns and Use Cases

### RAG Pattern (Retrieval Augmented Generation)
**When to use:**
- Need to ground responses in enterprise data
- Working with frequently changing information
- Require source attribution for responses
- Limited fine-tuning budget or expertise

**Implementation:**
1. Index custom data sources
2. Retrieve relevant context at query time
3. Include context in prompts
4. Generate grounded responses

### Fine-tuning
**When to use:**
- Need consistent tone or style
- Working with specialized terminology
- Require specific output formats
- Have sufficient training data

**Process:**
1. Prepare training dataset
2. Submit fine-tuning job
3. Evaluate model performance
4. Deploy custom model

### Chat Applications
**Components:**
- System message (instructions)
- Conversation history
- User input
- Response generation

**Best Practices:**
- Maintain conversation context
- Implement token management
- Handle errors gracefully
- Provide clear user feedback

## Integration Patterns

### SDK Integration
- Python SDK for backend services
- REST API for language-agnostic access
- Authentication via Azure credentials
- Connection string management

### Deployment Options
- Azure App Service for web applications
- Azure Functions for serverless
- Azure Container Apps for containerized solutions
- Static Web Apps for frontend applications

## Evaluation and Monitoring

### Key Metrics
- **Response quality**: Accuracy, relevance, coherence
- **Performance**: Latency, throughput
- **Cost efficiency**: Token usage, API calls
- **Safety**: Content filter triggers

### Testing Approaches
- Manual testing in playground
- Automated evaluation with test datasets
- A/B testing for prompt variations
- User feedback collection

## Learning Path Recommendations

### For Beginners
1. Complete Exercise 1 (Explore Azure AI Foundry)
2. Complete Exercise 2 (Model Catalog)
3. Complete Exercise 3 (Prompt Flow Chat)
4. Practice with chat playground
5. Build a simple chat application

### For Intermediate Developers
1. Review Exercises 1-3 as needed
2. Complete Exercise 4 (RAG)
3. Complete Exercise 2a (SDK)
4. Complete Exercise 7 (Evaluation)
5. Build a RAG-based knowledge bot

### For Advanced Users
1. Complete Exercise 5 (Fine-tuning)
2. Complete Exercise 6 (Content Filters)
3. Implement custom evaluation metrics
4. Integrate with enterprise systems
5. Build production-ready AI solutions

## Additional Resources

### Official Documentation
- [Azure AI Foundry Documentation](https://learn.microsoft.com/azure/ai-studio/) *(Note: Documentation is in transition from AI Studio to AI Foundry naming)*
- [Azure OpenAI Service Documentation](https://learn.microsoft.com/azure/ai-services/openai/)
- [Microsoft Learn Training Paths](https://learn.microsoft.com/training/paths/create-custom-copilots-ai-studio/)

### Community Resources
- GitHub Repository: [MicrosoftLearning/mslearn-ai-studio](https://github.com/MicrosoftLearning/mslearn-ai-studio)
- GitHub Pages: [Exercise Website](https://go.microsoft.com/fwlink/?linkid=2310724)
- GitHub Issues: Report problems in the exercises

### Related Technologies
- Prompt engineering techniques
- LangChain and other AI frameworks
- Vector databases (Azure AI Search, Cosmos DB)
- MLOps and AI lifecycle management

## Troubleshooting Common Issues

### Quota Limitations
- **Problem**: Model deployment fails due to quota limits
- **Solution**: Try a different region or request quota increase

### Rate Limiting
- **Problem**: API calls return 429 errors
- **Solution**: Implement exponential backoff, reduce TPM, or distribute load

### Content Filter Blocks
- **Problem**: Legitimate content gets filtered
- **Solution**: Review filter configuration, adjust sensitivity levels

### Performance Issues
- **Problem**: Slow response times
- **Solution**: Optimize prompts, reduce token counts, use caching

## Key Takeaways

1. **Azure AI Foundry provides a comprehensive platform** for building generative AI solutions with minimal infrastructure setup

2. **Model selection matters**: Choose between different models based on capability, cost, and latency requirements

3. **RAG is powerful**: Retrieval Augmented Generation enables AI models to work with custom, up-to-date data

4. **Content safety is crucial**: Always implement content filters for production applications

5. **Evaluation is essential**: Systematic testing and evaluation ensure quality and reliability

6. **Cost management requires attention**: Monitor usage and clean up resources to control costs

7. **Iterative development works best**: Start simple, test often, and incrementally add complexity

8. **SDK enables automation**: Programmatic access allows for CI/CD integration and advanced workflows

## Conclusion

The mslearn-ai-studio repository provides a practical, hands-on approach to learning Azure AI Foundry. By completing these exercises, developers gain experience with real-world AI development tasks, from basic model deployment to advanced techniques like RAG and fine-tuning. The exercises emphasize best practices, responsible AI principles, and production-ready patterns.

Whether you're building your first AI application or scaling enterprise solutions, these exercises provide valuable insights into the Azure AI ecosystem and modern generative AI development practices.

---

**Last Updated**: October 2024  
**Target Audience**: Developers, AI Engineers, Solution Architects  
**Difficulty Level**: Beginner to Advanced  
**Estimated Time**: 10-15 hours for all exercises
