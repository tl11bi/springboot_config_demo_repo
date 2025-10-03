# Spring Cloud Config Repository

This repository contains configuration files for Spring Cloud Config Server, organized using a folder-per-application layout with environment-specific profiles.

## Structure

- `common/` - Shared configuration files loaded for all applications
- `payment-service/` - Configuration files specific to the payment service
- `audit-service/` - Configuration files specific to the audit service

## Environments

- **dev** - Development environment
- **sit** - System Integration Testing environment  
- **pat** - Pre-production Acceptance Testing environment

## File Naming Convention

Configuration files follow the Spring Cloud Config naming convention:
- `{application}-{profile}.yml` for application-specific configurations
- `application.yml` and `application-{profile}.yml` for shared configurations

## Usage

To use the common configurations, add `common` to the `searchPaths` property in your Spring Cloud Config Server configuration.

Example Config Server setup:
```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: <this-repo-url>
          searchPaths: common,{application}
```

## Applications

### Payment Service
- Handles payment processing
- Uses PostgreSQL database
- Integrates with Kafka for event streaming
- Feature flags for new checkout functionality

### Audit Service  
- Manages audit logging and compliance
- Uses MongoDB for audit storage
- Configurable retention policies per environment