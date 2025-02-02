# JHC OpenMRS 3.0 Application

A containerized deployment of OpenMRS 3.0 with custom configurations for the JHC healthcare system.

## 🌐 Overview

This repository contains the build configuration for the JHC OpenMRS 3.0 application.

## 🚀 Quick Start

### Prerequisites

- Docker and Docker Compose
- Git
- OpenMRS user credentials

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/miirochristopher/jahdiel-org-emrs.git
   cd jahdiel-org-emrs
   ```

2. Set up environment variables:
   ```bash
   cp .env.example .env
   ```
   
3. Start the application:
   ```bash
   docker compose up --build
   ```

## 💾 Database Management

### Backup and Restore

To restore from a backup:

1. Place your SQL backup file in the `db` folder
2. Update the following configurations in `.env`:
   ```env
   OMRS_CONFIG_AUTO_UPDATE_DATABASE=false
   OMRS_CONFIG_CREATE_TABLES=false
   ```
3. Restart the application:
   ```bash
   docker compose down
   docker compose up --build
   ```

### Creating a Backup

```bash
docker exec jhc-mariadb mysqldump -u$MYSQL_USER -p$MYSQL_PASSWORD openmrs > backup_$(date +%Y%m%d).sql
```

## 🧹 Cleanup

To completely remove the application and its volumes:

```bash
docker compose -p jhc_emr down -v
```

## 🔧 Configuration

Key configuration files:

- `docker-compose.yml`: Container orchestration
- `.env`: Environment variables
- `db/`: Database initialization scripts

## 🛟 Troubleshooting

Common issues and solutions:

1. Database connection errors:
  - Verify MariaDB container is running
  - Ensure proper network connectivity

## 📚 Additional Resources

- [OpenMRS Documentation](https://wiki.openmrs.org/)
- [Docker Documentation](https://docs.docker.com/)
- [MariaDB Documentation](https://mariadb.org/documentation/)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request