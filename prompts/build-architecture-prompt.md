# Build Architecture Prompt

Based on the optimized SOP and integration specifications, design a comprehensive system architecture for the agent implementation.

## System Architecture Design

### Architecture Overview

**Architecture Style**: [Microservices / Monolithic / Serverless / Hybrid]
**Primary Pattern**: [Event-driven / Request-response / Pipeline / etc.]
**Deployment Target**: [Cloud / On-premise / Hybrid]

### High-Level Architecture Diagram
```
┌─────────────────┐     ┌─────────────────┐
│   User Input    │────▶│   API Gateway   │
└─────────────────┘     └────────┬────────┘
                                 │
                        ┌────────▼────────┐
                        │  Agent Core     │
                        │  ┌───────────┐  │
                        │  │Validation │  │
                        │  ├───────────┤  │
                        │  │Processing │  │
                        │  ├───────────┤  │
                        │  │Response   │  │
                        │  └───────────┘  │
                        └────────┬────────┘
                                 │
                ┌────────────────┼────────────────┐
                │                │                │
       ┌────────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
       │  Integration  │ │   Cache     │ │   Queue     │
       │   Services    │ │   Layer     │ │  Manager    │
       └───────────────┘ └─────────────┘ └─────────────┘
```

### Component Specifications

#### 1. API Gateway
**Purpose**: Entry point for all agent interactions
**Responsibilities**:
- Request routing
- Authentication/Authorization
- Rate limiting
- Request/Response transformation

**Technology Options**: [AWS API Gateway / Kong / Nginx]
**Key Configurations**:
- Rate limits: [X requests/min]
- Timeout: [Y seconds]
- CORS settings: [Configuration]

#### 2. Agent Core
**Purpose**: Main processing engine implementing SOP
**Subcomponents**:

##### 2.1 Input Validator
- Schema validation
- Business rule validation
- Security checks
- Error formatting

##### 2.2 Workflow Engine
- SOP implementation
- State management
- Decision execution
- Parallel processing coordinator

##### 2.3 Response Generator
- Output formatting
- Template engine
- Personalization logic
- Multi-format support

**Technology Stack**:
- Language: [Python / Node.js / Go]
- Framework: [FastAPI / Express / Gin]
- State Management: [Redis / In-memory]

#### 3. Integration Layer
**Purpose**: Manage all external system connections

**Components**:
- Connection pool manager
- Request queue
- Circuit breaker implementation
- Response cache

**Integration Adapters**:
- Adapter A: [External System 1]
- Adapter B: [External System 2]
- Adapter C: [External System 3]

#### 4. Data Layer
**Purpose**: Persistence and caching

**Cache Strategy**:
- L1 Cache: In-memory (application level)
- L2 Cache: Redis/Memcached
- L3 Cache: Database query cache

**Storage Requirements**:
- Operational data: [Database choice]
- Audit logs: [Storage solution]
- Analytics data: [Data warehouse]

#### 5. Queue Management
**Purpose**: Async processing and reliability

**Queue Types**:
- Priority queue for urgent requests
- Batch queue for bulk operations
- Dead letter queue for failures

**Technology**: [RabbitMQ / AWS SQS / Kafka]

### Data Flow Architecture

#### Synchronous Flow
1. Request arrives at API Gateway
2. Basic validation and auth
3. Route to appropriate handler
4. Process through workflow engine
5. Return response

#### Asynchronous Flow
1. Request queued for processing
2. Worker picks up from queue
3. Process through workflow
4. Store result
5. Notify callback/webhook

### Security Architecture

#### Authentication & Authorization
- Method: [OAuth2 / JWT / API Key]
- Token storage: [Approach]
- Permission model: [RBAC / ABAC]

#### Data Security
- Encryption at rest: [Method]
- Encryption in transit: [TLS 1.3]
- Sensitive data handling: [Approach]

### Scalability Design

#### Horizontal Scaling
- Stateless components: [List]
- Load balancing strategy: [Round-robin / Least connections]
- Auto-scaling triggers: [CPU / Memory / Queue depth]

#### Vertical Scaling
- Resource-intensive components: [List]
- Optimization strategies: [List]

### Monitoring and Observability

#### Metrics Collection
- Application metrics: [Prometheus / CloudWatch]
- Business metrics: [Custom dashboard]
- Infrastructure metrics: [Platform specific]

#### Logging Architecture
- Log aggregation: [ELK / CloudWatch Logs]
- Log levels and structure
- Retention policies

#### Tracing
- Distributed tracing: [Jaeger / X-Ray]
- Trace sampling strategy
- Critical path identification

### Deployment Architecture

#### Container Strategy
- Base images: [Specify]
- Container orchestration: [Kubernetes / ECS]
- Service mesh: [Istio / Linkerd] (if applicable)

#### CI/CD Pipeline
- Build process
- Test stages
- Deployment strategy: [Blue-green / Canary / Rolling]

### Disaster Recovery

#### Backup Strategy
- Data backup frequency
- Backup locations
- Recovery time objective (RTO)
- Recovery point objective (RPO)

#### Failover Design
- Multi-region deployment
- Health check configuration
- Automatic failover triggers

Generate a comprehensive architecture that can be directly used by development teams to build the system.