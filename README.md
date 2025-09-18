# CI/CD Learning Application 🚀

A real-world Node.js application demonstrating modern CI/CD practices with GitHub Actions.

## 📋 What You'll Learn

This project teaches CI/CD concepts through hands-on implementation:

- **Continuous Integration (CI)**: Automated testing, linting, security checks
- **Continuous Deployment (CD)**: Automated deployments to staging and production
- **Quality Gates**: Code coverage thresholds, security audits
- **Multi-environment Deployments**: Staging → Production pipeline
- **Rollback Strategies**: Hotfix deployments and emergency procedures
- **Containerization**: Docker for consistent deployments

## 🏗️ Application Architecture

Simple REST API with the following endpoints:

- `GET /health` - Health check endpoint
- `GET /api/users` - List all users
- `GET /api/users/:id` - Get specific user
- `POST /api/users` - Create new user

## 🔄 CI/CD Pipeline Overview

### Continuous Integration (CI)
Triggered on: Push to `main`/`develop`, Pull Requests

1. **Code Quality Checks**
   - ESLint for code style
   - Security audit with npm audit
   - Multi-version Node.js testing (18.x, 20.x)

2. **Testing**
   - Unit tests with Jest
   - Integration tests with Supertest
   - Code coverage reporting (80% threshold)

3. **Build**
   - Production build creation
   - Artifact storage for deployment

### Continuous Deployment (CD)
Triggered on: Successful CI completion on `main` branch

1. **Staging Deployment**
   - Automatic deployment to staging environment
   - Smoke tests execution
   - Team notifications

2. **Production Deployment**
   - Manual approval required (GitHub Environments)
   - Health checks post-deployment
   - Automatic release creation

### Hotfix Pipeline
Triggered on: Push to `hotfix/*` branches or manual dispatch

- Fast-track deployment for critical fixes
- Minimal testing (critical tests only)
- On-call team notifications

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ 
- npm or yarn
- Docker (optional)

### Local Development

1. **Clone and install**
   ```bash
   git clone <your-repo>
   cd cicd-learning-app
   npm install
   ```

2. **Set up environment**
   ```bash
   cp .env.example .env
   ```

3. **Run the application**
   ```bash
   npm run dev
   ```

4. **Run tests**
   ```bash
   npm test
   npm run test:coverage
   ```

5. **Run linting**
   ```bash
   npm run lint
   npm run lint:fix
   ```

### Docker Development

```bash
# Build and run with Docker Compose
docker-compose up --build

# Or build and run manually
docker build -t cicd-app .
docker run -p 3000:3000 cicd-app
```

## 🧪 Testing the API

```bash
# Health check
curl http://localhost:3000/health

# Get all users
curl http://localhost:3000/api/users

# Get specific user
curl http://localhost:3000/api/users/1

# Create new user
curl -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com"}'
```

## 📊 CI/CD Best Practices Demonstrated

### 1. **Quality Gates**
- Code coverage thresholds (80%)
- Security vulnerability scanning
- Linting and code style enforcement

### 2. **Environment Strategy**
- Development → Staging → Production flow
- Environment-specific configurations
- Manual approval for production deployments

### 3. **Testing Strategy**
- Unit tests for individual functions
- Integration tests for API endpoints
- Smoke tests for deployment verification

### 4. **Security**
- Dependency vulnerability scanning
- Non-root Docker user
- Environment variable management

### 5. **Monitoring & Observability**
- Health check endpoints
- Application logging
- Deployment notifications

## 🔧 Pipeline Configuration

### GitHub Environments Setup

1. Go to Settings → Environments
2. Create `staging` and `production` environments
3. Add protection rules for production:
   - Required reviewers
   - Wait timer
   - Deployment branches restriction

### Required Secrets

Add these to your GitHub repository secrets:

```
GITHUB_TOKEN (automatically provided)
```

For real deployments, you'd also add:
```
DEPLOY_HOST
DEPLOY_USER
DEPLOY_KEY
SLACK_WEBHOOK_URL
```

## 📈 Monitoring Your Pipeline

### GitHub Actions Dashboard
- View workflow runs and status
- Download build artifacts
- Review deployment history

### Key Metrics to Track
- Build success rate
- Test coverage trends
- Deployment frequency
- Mean time to recovery (MTTR)

## 🚨 Troubleshooting

### Common Issues

1. **Tests failing in CI but passing locally**
   - Check Node.js version differences
   - Verify environment variables
   - Review test isolation

2. **Deployment failures**
   - Check artifact availability
   - Verify environment configurations
   - Review deployment logs

3. **Coverage threshold failures**
   - Add missing tests
   - Review coverage reports
   - Adjust thresholds if needed

## 🎯 Next Steps

To extend this learning project:

1. **Add a real database** (PostgreSQL, MongoDB)
2. **Implement authentication** (JWT, OAuth)
3. **Add monitoring** (Prometheus, Grafana)
4. **Set up logging** (Winston, ELK stack)
5. **Add performance testing** (Artillery, k6)
6. **Implement blue-green deployments**
7. **Add infrastructure as code** (Terraform, CloudFormation)

## 📚 Learning Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Docker Best Practices](https://docs.docker.com/develop/dev-best-practices/)
- [Jest Testing Framework](https://jestjs.io/docs/getting-started)
- [Express.js Guide](https://expressjs.com/en/guide/routing.html)

---

**Happy Learning!** 🎉 This project gives you hands-on experience with real CI/CD practices used in production environments.