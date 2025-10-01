---
title: "Auction Service"
weight: 4
#date: 2023-02-01
tags: ["Go","Postgresql","docker", "CI/CD", "Divar"]
author: ["By: Rayhaneh Einollahi, Sana Mousavi, Zahra Hosseini"]
description: "Auction Service is a Go app that lets post owners create auctions and users place bids. It integrates with Divar for login, handles auctions and bids securely, and tracks everything with JWT-based auth. Simple, reliable, and ready to run locally or in Docker." 
summary: "Auction Service is a Go app that lets post owners create auctions and users place bids. It integrates with Divar for login, handles auctions and bids securely, and tracks everything with JWT-based auth. Simple, reliable, and ready to run locally or in Docker." 
cover:
  image: "image.jpg"
  alt: "image"
  relative: false
#editPost:
 #   URL: "https://doi.org/10.1073/pnas.1816454115"
 #   Text: "Other Journal Name"

---
**Team Lead:** Sajjad Sanikhani

---
## Introduction
The Auction Service is a Go-based application that integrates with Divar's OpenPlatform to enable post owners to create auctions for their listings and allow other users to place bids. The system authenticates users through OAuth, manages auction lifecycles, and tracks bidding activity.
#### Key Features:
- OAuth integration with Divar
- Role-based access (post owners vs. viewers)
- Auction creation and management
- Bidding system
- JWT-based authentication
- Sentry error reporting

## System Architecture
The application follows a clean architecture approach with the following components:
- HTTP Server - Handles incoming requests and renders HTML templates
- Services Layer - Contains business logic for auctions, bids, users, and posts
- Data Access Layer - Uses sqlc-generated code for type-safe database queries
- External Integration - Connects with Divar's OpenPlatform API

## Project Structure
```bash
.
├──  cmd/  # Application entry points
│  └──  server/  # Main server executable
├──  configs/  # Configuration files
├──  internal/  # Private application code
│  ├──  bidding/  # Auction and bidding logic
│  │  ├──  models/  # Database models for bidding
│  │  └──  services/  # Business logic for auctions/bids
│  ├──  clients/  # External API clients
│  ├──  config/  # Configuration structures
│  ├──  httpServer/  # HTTP handlers and middleware
│  ├──  oauth/  # OAuth service
│  ├──  posts/  # Post-related functionality
│  ├──  user/  # User models
│  └──  users/  # User services
├──  pkg/  # Reusable packages
│  ├──  auth/  # JWT authentication
│  ├──  database/  # Database connection handling
│  └──  error_report/  # Sentry integration
└──  templates/  # HTML templates
```
## Installation & Setup

#### Prerequisites
- Go 1.22+
- PostgreSQL 14+
- Docker (optional)
- ngrok (for local development with Divar integration)
- sentry dns (if `sentry_enabled: true` in config)

#### Setting Up the Development Environment
1-  Clone the repository
2- Install dependencies:
```bash
make  dependencies
```
3- Set up the local database:
```
make setup_local
```
This will start a PostgreSQL instance in Docker with the following configuration:
- Host: localhost
- Port: 5432
- User: bid_user
- Password: secret

- Database: bid_db
## Configuration
The application is configured through a YAML file. Create your configuration by copying the example:
```bash
cp  configs/config.example.yaml  configs/config.yaml
```
#### Configuration Options
```yaml
database:
host: "localhost"  # Database host
port: 5432  # Database port
username: "bid_user"  # Database username
password: "securepassword"  # Database password
dbname: "bid_db"  # Database name
sslmode: "disable"  # SSL mode for database connection
maxconns: 10  # Maximum database connections
minconns: 2  # Minimum database connections
maxconnlifetimejitterminutes: 5  # Connection lifetime jitter
maxconnlifetimeminutes: 60  # Maximum connection lifetime
maxconnnidletimeminutes: 30  # Connection idle timeout
openplatform:
api_key: "<divar API Key>"  # Divar API key
oauth_secret: "<oauth secret>"  # Divar OAuth secret
app_slug: "<app slug>"  # Divar app slug
base_url: "<ngrok static domain>"  # Public URL for callbacks
server:
port: <port>  # Server port
jwt:
secretKey: "jwt_secret_key"  # JWT secret key
expiryDuration: 24  # JWT expiry in hours
logging:
sentry_enabled: false  # Enable Sentry error reporting
sentry_dsn: ""  # Sentry DSN
level: info  # Logging level
```
## Running the Application
#### Local Development
1. Make sure your PostgreSQL database is running
2. Start the application:
```bash
make  run
# or
go  run  ./cmd/server  serve  --configFile  ./configs/config.yaml
```
3. For Divar integration, expose your local server using ngrok:
``` bash
ngrok  http  --url=r<ngrock-static-domain> <port>
```
4. Access the application at in divar new extention setup:
```
https://<replace base_url(for example ngrok-static-domain)>/oauth2/user-auth/
https://<replace base_url(for example ngrok-static-domain)>/oauth2/user-callback/
```
#### Building the Binary
```bash
make  build
```
The binary will be generated in the `.bin` directory.
## Authentication Flow
1. Users are redirected from Divar to the application via OAuth:
	- Initial URL: `/oauth2/user-auth/`
	- Callback URL: `/oauth2/user-callback/`
2. After authentication:
	- Post owners can create auctions or view existing bids
	- Viewers can place bids if an auction exists for the post

- JWT tokens are used for authorization
## Development
#### Generating SQL Code
The project uses `sqlc` for type-safe SQL:
```bash
make  generate_sql
```
#### Running Tests
```bash
make  test
```
### Linting & Formatting
```bash
make  lint  # Run linter
make  lint-fix  # Fix linting issues
make  fmt  # Format code
```
## Docker Deployment
#### Building the Docker Image
```bash
docker  build  -t  auction-app  .
```
#### Running the Container
```bash
docker  run  -p <port>:8080  -v /path/to/config.yaml:/srv/build/configs/config.yaml auction-app
```

#### Docker Image Details

The Docker build process uses a multi-stage approach:
1. Build stage using Go 1.22 to compile the application

2. Runtime stage using Ubuntu 22.04 with minimal dependencies

  

## Troubleshooting
#### Common Issues
1. Database Connection Problems
	- Check PostgreSQL is running and accessible

	- Verify database credentials in config.yaml

2. Divar Integration Issues

  

	- Ensure ngrok is properly forwarding to your local server

	- Verify the OAuth redirect URL matches exactly what's configured in Divar

3. Sentry Error Reporting

  

	- If enabled, check the DSN is correctly configured

	- Test error reporting by triggering a non-critical error

#### Logs
- Check application logs for detailed error information. When Sentry is enabled, errors will also be reported to the Sentry dashboard.
- uses `request_id` and `flow_id` to track requests.

  
------------------
For additional support or to report issues, please contact the development team.

---
<a href="https://github.com/Rayhaneh-Einollahi/Auction_Service" target="_blank" rel="noopener" 
   style="display:inline-block; padding:12px 24px; font-weight:bold; background-color:#24292e; 
          color:white; border-radius:8px; text-decoration:none; font-size:16px;">
  ⭐ Star on GitHub
</a>

---


