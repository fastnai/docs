# Glossary

### API (Application Programming Interface)

A set of protocols and tools for building and interacting with software applications. Fastn provides APIs to manage integrations, users, and workflows.

### CLI (Command Line Interface)

A text-based interface to interact with Fastn, allowing developers to run commands, trigger actions, and manage integrations via terminal.

### Connect Portal

A customizable UI that allows end users to connect third-party applications to your platform securely.

### Embed Fastn UCL (Unified Context Layer)

Fastn’s core orchestration engine that unifies integrations under a single JSON API or SDK call, supporting multi-tenant environments with secure routing and execution.

### Integration Hub

A centralized platform within Fastn where users can connect, manage, and monitor all their integrations and AI-driven workflows.

### Multitenancy

An architecture where a single instance of Fastn serves multiple tenants (customers), ensuring complete data isolation and secure execution for each tenant.

### Orchestration Layer

The unified layer that manages communication, execution, and routing between AI agents and connected apps or services in Fastn.

### Policy Control

Rules and permissions that govern what actions AI agents or users can perform within the Fastn platform.

### SDK (Software Development Kit)

A set of tools, libraries, and documentation provided by Fastn to help developers embed and extend Fastn functionality within their applications.

### Server-Sent Events (SSE)

A communication protocol supported by Fastn for real-time streaming of updates from the server to the client.

### Workflow

A sequence of automated tasks or actions designed in Fastn to synchronize, transform, or route data across multiple applications.

### **Agent Connect UI**

A plug-and-play embeddable interface (React component) provided by Fastn UCL that allows users to interact with connected tools and actions directly in your app interface.

### **AI Agent**

A component in Fastn Flows that maintains context, interprets user input, and interacts with external systems via enabled actions. It leverages the MCP layer and OpenAI models to perform reasoning or task execution.

### **AI Action**

A flow step where AI performs a task using the input from previous steps. These can include summarization, classification, or generating commands for connected tools.

### **Connector**

A prebuilt integration with third-party apps (e.g., Notion, Jira, Slack). Connectors handle OAuth, token management, and expose available actions that can be executed in flows or via agents.

### **Workspace**

A logical grouping within Fastn UCL that contains connectors, actions, and environment configurations for a specific app, tenant, or team. Each workspace has a unique Space ID and supports isolation.

### **Tenant ID**

An identifier used to distinguish individual tenants (customers or users) within a single workspace. Enables Fastn UCL to provide secure multitenancy and ensure context-aware execution of actions.

### **MCP (Model Context Protocol)**

An open protocol that standardizes how AI agents describe actions and interact with external tools. Fastn UCL builds on top of MCP to make it production-ready by adding infrastructure, security, and multitenant context handling.

### **MCP Server URL**

The endpoint that agents use to send and receive structured action commands. Fastn provides a preconfigured MCP server (via `NEXT_PUBLIC_FASTN_MCP_SERVER_URL`) for routing, authentication, and context.

### **Action**

A predefined operation exposed by a connector (e.g., “Get Tasks” in Notion or “Send Message” in Slack). Actions are selectable per connector and executable through agents or flows.

### **Environment File (.env)**

A local configuration file in your codebase that stores sensitive variables such as your OpenAI key and Fastn MCP server URL.

### **Flow**

A no-code/low-code visual automation built inside Fastn that sequences steps like triggers, connectors, AI agents, and logic to perform a complete task.

### **Flow Types**

Different kinds of flows tailored to use cases like scheduled execution, webhook-based flows, or agent-driven flows.

### **Trigger**

The starting point of a flow. It defines the condition or event that initiates the flow, such as a time-based schedule, webhook, or external command.

### **Variables & States**

Used within flows to store and pass data between steps. Variables are static, while states are updated dynamically during flow execution.

### **Multitenancy**

The architecture in Fastn UCL that allows multiple tenants to securely share the same infrastructure while maintaining strict separation of data, context, and configuration.

### **Space ID**

A unique identifier for each Fastn UCL workspace, embedded within the MCP Server URL and used for scoping connector access and tenant isolation.

### **Agent Instruction**

The natural language prompt or command that the AI Agent interprets to select the appropriate action and execute it via Fastn UCL.

### **Connected Status**

Indicates a successful OAuth or API connection to a third-party app. Once a connector shows "Connected" in the UI, its actions can be selected and used.

### **Codespaces (GitHub)**

A browser-based cloud development environment that allows users to run Fastn UCL integration projects without needing to install dependencies locally.
