# KnowBot - Your Enterprise Knowledge at Your Fingertips
 
## Project Overview
<img width="800" height="244" alt="image" src="https://github.com/user-attachments/assets/a883c738-cba4-4f9e-b5bb-36e5df35a1e6" />

• **Core Value Proposition**: Transforms scattered enterprise knowledge into instant, conversational answers through natural language queries

• **Primary Capability**: Provides intelligent responses from Confluence and SharePoint repositories using MuleSoft's Anypoint Code Builder and AI integration

• **Target Users**: Enterprise knowledge workers seeking efficient access to organizational documentation and resources

 
## Inspiration and Problem Statement
• **Root Issue**: Despite significant investment in knowledge management platforms, information retrieval remained inefficient and time-consuming

• **Strategic Opportunity**: Leveraged MuleSoft integration capabilities with Model Context Protocol to create intelligent orchestration layer

• **Design Philosophy**: Enhanced existing knowledge systems rather than replacing them through natural language accessibility

 
## Technology Stack Components
• **Core Integration Platform**: MuleSoft serves as the central processing brain for KnowBot operations

• **Frontend Interface**: React-based user interface for query submission and result presentation

• **Development Environment**: Anypoint Code Builder for visual flow design and implementation

• **Knowledge Sources**: Confluence and SharePoint repositories for enterprise content retrieval

• **AI Processing Engine**: Mistral AI for natural language understanding and content analysis

• **Protocol Integration**: MCP implementation using Cursor for enhanced AI capabilities

 
## Anypoint Code Builder Implementation
• **Architecture Approach**: API-first design methodology with API-led connectivity principles

• **SharePoint Integration**: Dedicated connector for document library access and content retrieval

• **Confluence Integration**: HTTP Request component for external confluence rest api service

• **Performance Optimization**: Object Store implementation for caching frequently accessed content

• **AI Interface**: MCP Connector for seamless integration with artificial intelligence services
 
## Primary Flow Architecture
<img width="773" height="703" alt="image" src="https://github.com/user-attachments/assets/8a6d7c7c-fe15-4d27-a921-9fb2d0cdaca5" />

• **Entry Point Function**: MCP Tool Listener component configured with Server-Sent Events connectivity

• **Endpoint Configuration**: Accessible through /mcp-demo endpoint for structured tool requests

• **Processing Delegation**: Routes requests to appropriate sub-flows based on knowledge source requirements

• **Platform Coverage**: Handles both Confluence and SharePoint system queries through unified interface

• **Response Management**: Returns processed results to MCP clients in standardized response format

 
## Confluence Processing Workflow
• **Stage One - Query Analysis**: Natural language prompts forwarded to Mistral AI for intelligent keyword extraction

• **Search Construction**: Confluence Query Language URL construction using extracted keywords

• **API Integration**: Authenticated HTTP GET requests to Confluence REST API endpoint

• **Search Pattern**: CQL pattern implementation using title~'keyword' against india.atlassian.net instance

• **AI-Powered Filtering**: Original query and retrieved page titles submitted to Mistral AI for relevance analysis

• **Handling Large Result Sets**: Manages scenarios when Confluence searches exceed default page size limitations

• **Response Assembly**: Structured JSON format consolidation including page titles, cleaned content, and source attribution

 
## SharePoint Processing Workflow
• **Document Analysis Focus**: Implements intelligent document analysis and summarization for SharePoint document libraries

• **Keyword Extraction**: Mistral AI services process natural language queries to identify relevant business and technical terms

• **OData Query Construction**: SharePoint connector executes filtered queries against specified document library paths

• **Performance Optimization**: Efficient document content retrieval while maintaining system performance standards

• **Content Analysis**: AI examination of JSON and CSV file contents with comprehensive summary generation

• **Analysis Components**: Data structure analysis, content categorization, key field identification, and record counting

• **Output Format**: Structured analytical results in JSON format with file-level analysis and statistical information

 
## Project Impact and Measurable Outcomes
• **Time Efficiency**: Knowledge discovery time reduction from hours to minutes for enterprise users

• **System Unification**: Unified access provision to multiple enterprise systems through single interface

• **Contextual Intelligence**: Delivery of contextual answers with proper source attribution for information verification

• **Scalability**: System design capable of handling thousands of concurrent user requests

• **Performance Validation**: Successful demonstration of intelligent knowledge orchestration capabilities during hackathon

 
## Future Development Roadmap
• **Platform Expansion**: Integration extension to additional source systems including Jira and ServiceNow

• **AI Enhancement**: Implementation of advanced AI features incorporating user feedback learning capabilities

• **Mobile Development**: Mobile application development utilizing existing API foundation

• **Analytics Implementation**: Dashboard creation for tracking knowledge gaps and usage pattern analysis

• **Proactive Capabilities**: Development of knowledge sharing features that suggest relevant information proactively

• **Knowledge Graph Development**: Relationship mapping between different enterprise content pieces

• **Expert Identification**: System development connecting users with human experts when AI assistance proves insufficient

 
## Strategic Conclusion
• **Integration Philosophy**: Powerful AI applications emerge from intelligent layers connecting existing enterprise tools rather than standalone systems

• **Technology Combination**: Robust integration platforms combined with sophisticated data transformation and emerging AI protocols

• **Value Unlocking**: Organizations can unlock knowledge asset value without requiring extensive machine learning expertise

• **Future Vision**: Enterprise knowledge management evolution toward intelligent orchestration understanding context and usage patterns

• **Implementation Validation**: Hackathon experience demonstrated achievable capabilities using existing enterprise integration platforms with emerging AI technologies

## Challenges Faced
 
### Cursor (MCP Configuration)
- When using Cursor, it is necessary to interact through the **Model Context Protocol (MCP)**—without this, Cursor often prefers to launch actions via its embedded browser or directly point to a website instead of calling the custom tool.
- The MCP setup in Cursor requires configuring your `mcp.json` file and ensuring the tool is registered through **Settings > Developer > Edit Config > MCP Tools** and by adding a “Custom MCP”. Without proper MCP registration, Cursor does not route prompts to the intended backend service and defaults to in-app browser/web queries first.
 
### Upload to Cloud / Confluence 403 Forbidden
- When attempting to fetch details or upload/fetch documents from Confluence, the system returned a **403 Forbidden error**.
- This typically indicates issues such as:
  - Missing or invalid authentication/authorization credentials (API tokens/keys not present or invalid).
  - The service account or API user lacks required permissions on the Confluence site or the target content.
  - Confluence space or document-level restrictions are preventing access even with valid credentials.
- To resolve, verify:
  - The correct API token or OAuth credentials are supplied in the request header.
  - The user has necessary permissions on both Confluence and the specific space/page being accessed.
  - Network policies or admin settings are not blocking API access for third-party apps.
 
**Summary:**  
MCP must be correctly configured for effective Cursor integration, and Confluence access failures are often permission or authentication related. Both areas must be set up and tested thoroughly to avoid redirection or API errors in enterprise automation projects.
