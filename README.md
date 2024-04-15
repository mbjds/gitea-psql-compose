# Gitea Docker Compose Configuration

This repository contains a Docker Compose configuration file to set up a Gitea instance along with a PostgreSQL database.

## Prerequisites

Before running the Docker Compose setup, make sure you have Docker and Docker Compose installed on your system.

## Usage

1. Clone this repository to your local machine:

```bash
git clone <repository-url>

2. Navigate to the directory containing the `docker-compose.yml` file:

```bash
cd <repository-directory>
```

3. Run Docker Compose to start the Gitea service:

```bash
docker-compose up -d
```

This command will start the Gitea and PostgreSQL containers in the background. You can now access your Gitea instance at `http://localhost:3000` in your web browser.

## Configuration

The `docker-compose.yml` file in this repository defines the configuration for the Gitea and PostgreSQL containers. Here's a brief overview:

### Gitea Service

- **Image**: gitea/gitea:latest
- **Container Name**: gitea
- **Ports**: 
  - 3000:3000 (Gitea web interface)
  - 22:22 (SSH access)
- **Environment Variables**:
  - DB_TYPE=postgres
  - DB_HOST=db:5432
  - DB_NAME=gitea
  - DB_USER=gitea
  - DB_PASSWD=git21Ta33teea
  - USER_UID=1000
  - USER_GID=1000
- **Volumes**:
  - ./git_data:/data
  - /etc/timezone:/etc/timezone:ro
  - /etc/localtime:/etc/localtime:ro
- **Dependencies**:
  - db

### PostgreSQL Service

- **Image**: postgres:alpine
- **Container Name**: postgres
- **Environment Variables**:
  - POSTGRES_USER=gitea
  - POSTGRES_PASSWORD=git21Ta33teea
  - POSTGRES_DB=gitea
- **Volumes**:
  - ./db_data:/var/lib/postgresql/data
- **Exposed Port**:
  - 5432 (PostgreSQL)

## License

This Docker Compose configuration is licensed under the [MIT License](LICENSE).
```

