# Build Deployment Prompt

Based on the system architecture and implementation, create comprehensive deployment documentation and configuration files for production deployment.

## Deployment Guide Generation

Create complete deployment documentation that covers all aspects of getting the agent into production:

### Deployment Guide (deployment-guide.md)

```markdown
# Production Deployment Guide

## Overview
This guide covers deploying the generated AI agent to production environments with proper monitoring, scaling, and security configurations.

## Architecture Overview

### Components
- **Agent Core**: Main application server
- **Integration Layer**: External service connections
- **Cache Layer**: Performance optimization
- **Database**: Persistent storage (if required)
- **Load Balancer**: Traffic distribution
- **Monitoring**: Health checks and metrics

### Technology Stack
- **Runtime**: Python 3.9+
- **Web Framework**: FastAPI
- **ASGI Server**: Uvicorn
- **Container**: Docker
- **Orchestration**: Kubernetes (recommended) or Docker Compose
- **Cache**: Redis
- **Database**: PostgreSQL (if required)
- **Monitoring**: Prometheus + Grafana

## Pre-deployment Requirements

### System Requirements
- **CPU**: Minimum 2 cores, Recommended 4+ cores
- **Memory**: Minimum 4GB, Recommended 8GB+
- **Storage**: Minimum 10GB, Recommended 50GB+
- **Network**: Outbound HTTPS access to external APIs

### Dependencies
- Docker 20.10+
- Kubernetes 1.20+ (for K8s deployment)
- kubectl configured
- Helm 3.0+ (optional, for package management)

## Configuration

### Environment Variables
Create a `.env` file with the following variables:

```bash
# Agent Configuration
AGENT_NAME=Production-Agent
AGENT_VERSION=1.0.0
DEBUG_MODE=false
LOG_LEVEL=INFO

# Server Configuration
HOST=0.0.0.0
PORT=8000
WORKERS=4

# External Integrations
EXAMPLE_API_URL=https://api.example.com
EXAMPLE_API_KEY=your_api_key_here
DATABASE_URL=postgresql://user:pass@localhost:5432/db

# Cache Configuration
REDIS_URL=redis://localhost:6379/0
CACHE_TTL=300

# Security
SECRET_KEY=your_secret_key_here
ALLOWED_HOSTS=["localhost", "your-domain.com"]

# Performance
MAX_RETRIES=3
TIMEOUT=30
RATE_LIMIT=100

# Monitoring
METRICS_ENABLED=true
PROMETHEUS_PORT=9090
```

### Configuration Files

#### Docker Configuration (Dockerfile)
```dockerfile
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements and install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Create non-root user
RUN useradd -m -u 1000 agent && chown -R agent:agent /app
USER agent

# Expose port
EXPOSE 8000

# Health check
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:8000/health || exit 1

# Start application
CMD ["uvicorn", "agent_core:app", "--host", "0.0.0.0", "--port", "8000"]
```

#### Docker Compose (docker-compose.yml)
```yaml
version: '3.8'

services:
  agent:
    build: .
    ports:
      - "8000:8000"
    environment:
      - REDIS_URL=redis://redis:6379/0
      - DATABASE_URL=postgresql://postgres:password@postgres:5432/agent_db
    depends_on:
      - redis
      - postgres
    volumes:
      - ./logs:/app/logs
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8000/health"]
      interval: 30s
      timeout: 10s
      retries: 3

  redis:
    image: redis:6-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data
    restart: unless-stopped

  postgres:
    image: postgres:13
    environment:
      - POSTGRES_DB=agent_db
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=password
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    restart: unless-stopped

  prometheus:
    image: prom/prometheus
    ports:
      - "9090:9090"
    volumes:
      - ./monitoring/prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus_data:/prometheus
    restart: unless-stopped

  grafana:
    image: grafana/grafana
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_PASSWORD=admin
    volumes:
      - grafana_data:/var/lib/grafana
    restart: unless-stopped

volumes:
  redis_data:
  postgres_data:
  prometheus_data:
  grafana_data:
```

## Deployment Options

### Option 1: Docker Compose (Simple Deployment)

#### Prerequisites
- Docker and Docker Compose installed
- Domain name configured (optional)

#### Deployment Steps
1. **Clone Repository**
   ```bash
   git clone <repository-url>
   cd agent-deployment
   ```

2. **Configure Environment**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Build and Start Services**
   ```bash
   docker-compose up -d
   ```

4. **Verify Deployment**
   ```bash
   curl http://localhost:8000/health
   ```

5. **View Logs**
   ```bash
   docker-compose logs -f agent
   ```

### Option 2: Kubernetes (Production Deployment)

#### Kubernetes Manifests

##### Namespace (namespace.yaml)
```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: agent-system
```

##### ConfigMap (configmap.yaml)
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: agent-config
  namespace: agent-system
data:
  AGENT_NAME: "Production-Agent"
  LOG_LEVEL: "INFO"
  DEBUG_MODE: "false"
  HOST: "0.0.0.0"
  PORT: "8000"
```

##### Secret (secret.yaml)
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: agent-secrets
  namespace: agent-system
type: Opaque
data:
  SECRET_KEY: <base64-encoded-secret>
  API_KEY: <base64-encoded-api-key>
```

##### Deployment (deployment.yaml)
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: agent
  namespace: agent-system
spec:
  replicas: 3
  selector:
    matchLabels:
      app: agent
  template:
    metadata:
      labels:
        app: agent
    spec:
      containers:
      - name: agent
        image: your-registry/agent:latest
        ports:
        - containerPort: 8000
        envFrom:
        - configMapRef:
            name: agent-config
        - secretRef:
            name: agent-secrets
        resources:
          requests:
            memory: "512Mi"
            cpu: "250m"
          limits:
            memory: "1Gi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 8000
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /health
            port: 8000
          initialDelaySeconds: 5
          periodSeconds: 5
```

##### Service (service.yaml)
```yaml
apiVersion: v1
kind: Service
metadata:
  name: agent-service
  namespace: agent-system
spec:
  selector:
    app: agent
  ports:
  - port: 80
    targetPort: 8000
  type: ClusterIP
```

##### Ingress (ingress.yaml)
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: agent-ingress
  namespace: agent-system
  annotations:
    kubernetes.io/ingress.class: nginx
    cert-manager.io/cluster-issuer: letsencrypt-prod
spec:
  tls:
  - hosts:
    - agent.yourdomain.com
    secretName: agent-tls
  rules:
  - host: agent.yourdomain.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: agent-service
            port:
              number: 80
```

#### Kubernetes Deployment Steps
1. **Apply Manifests**
   ```bash
   kubectl apply -f namespace.yaml
   kubectl apply -f configmap.yaml
   kubectl apply -f secret.yaml
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   kubectl apply -f ingress.yaml
   ```

2. **Verify Deployment**
   ```bash
   kubectl get pods -n agent-system
   kubectl logs -f deployment/agent -n agent-system
   ```

## Monitoring and Logging

### Prometheus Configuration (prometheus.yml)
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'agent'
    static_configs:
      - targets: ['agent:8000']
    metrics_path: '/metrics'
```

### Grafana Dashboard
Import the provided Grafana dashboard JSON for agent monitoring.

### Log Configuration
- **Format**: JSON structured logging
- **Level**: INFO for production, DEBUG for development
- **Rotation**: Daily rotation with 30-day retention
- **Aggregation**: Centralized logging with ELK stack or similar

## Security Considerations

### SSL/TLS Configuration
- Use HTTPS for all external communications
- Configure proper SSL certificates
- Enable HSTS headers

### API Security
- Implement rate limiting
- Use API key authentication
- Validate all inputs
- Enable CORS appropriately

### Container Security
- Use non-root user in containers
- Scan images for vulnerabilities
- Keep base images updated
- Implement network policies in Kubernetes

## Performance Optimization

### Scaling Configuration
- **Horizontal Pod Autoscaler** (Kubernetes):
  ```yaml
  apiVersion: autoscaling/v2
  kind: HorizontalPodAutoscaler
  metadata:
    name: agent-hpa
    namespace: agent-system
  spec:
    scaleTargetRef:
      apiVersion: apps/v1
      kind: Deployment
      name: agent
    minReplicas: 3
    maxReplicas: 10
    metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
  ```

### Cache Configuration
- Redis cluster for high availability
- Appropriate TTL settings
- Cache warming strategies

## Maintenance and Updates

### Zero-Downtime Deployment
1. Build new image with version tag
2. Update deployment with new image
3. Kubernetes rolling update automatically manages transition
4. Verify new version health
5. Rollback if issues detected

### Backup Strategy
- Database backups (if applicable)
- Configuration backups
- Log archival
- Disaster recovery procedures

## Troubleshooting

### Common Issues
1. **High Memory Usage**
   - Increase memory limits
   - Check for memory leaks
   - Optimize cache usage

2. **Integration Timeouts**
   - Check external service health
   - Adjust timeout configurations
   - Implement circuit breakers

3. **High CPU Usage**
   - Increase CPU limits
   - Optimize processing algorithms
   - Scale horizontally

### Diagnostic Commands
```bash
# Check pod status
kubectl get pods -n agent-system

# View logs
kubectl logs -f deployment/agent -n agent-system

# Check resource usage
kubectl top pods -n agent-system

# Port forward for debugging
kubectl port-forward svc/agent-service 8000:80 -n agent-system
```

## Production Checklist

Before going live, ensure:
- [ ] All environment variables configured
- [ ] Security certificates installed
- [ ] Monitoring and alerting set up
- [ ] Backup procedures tested
- [ ] Load testing completed
- [ ] Disaster recovery plan documented
- [ ] Team training completed
- [ ] Documentation updated
- [ ] Rollback procedures tested
- [ ] Performance benchmarks established

## Support and Maintenance

### Monitoring Alerts
Set up alerts for:
- High error rates (>5%)
- High response times (>2 seconds)
- Low success rates (<95%)
- Resource usage (>80% CPU/memory)
- External service failures

### Regular Maintenance
- Weekly security updates
- Monthly performance reviews
- Quarterly disaster recovery tests
- Annual architecture reviews

This deployment guide ensures a robust, scalable, and maintainable production deployment of your AI agent.
```

Generate comprehensive deployment documentation that covers all aspects of production deployment with proper security, monitoring, and maintenance procedures.