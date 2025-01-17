# WordPress Docker Documentation

Welcome to the WordPress Docker documentation! This guide walks you through the setup and enhancement of a WordPress environment using Docker, from basic configurations to advanced features.

## Versions and Features

### Version 1.x: Basic Setup and Essential Features
- [v1.0.0: Basic Docker Compose Setup](v1.0.0-basic-docker-compose.md)  
  Learn how to set up WordPress and MySQL using Docker Compose.

- [v1.1.0: Manage Credentials Outside Compose File](v1.1.0-manage-credentials.md)  
  Move sensitive information out of the `docker-compose.yml` file and into an `.env` file for better security.

- [v1.2.0: Backup and Restore Functionality](v1.2.0-backup-restore.md)  
  Add backup and restore capabilities for both the database and WordPress content.

### Version 2.x: Networking and Advanced Features
- [v2.0.0: Create Public and Private Networks](v2.0.0-public-private-network.md)  
  Separate public and private services using Docker networks for enhanced security.

- [v2.1.0: Add Monitoring](v2.1.0-add-monitoring.md)  
  Integrate monitoring tools to track the health and performance of your containers.

- [v2.2.0: Add Web Containers with DNS Round-Robin](v2.3.0-web-dns-round-robin.md)  
  Use DNS round-robin to distribute traffic across multiple web containers.

- [v2.3.0: Implement a Load Balancer with Sticky Sessions](v2.4.0-load-balancer-sticky-sessions.md)  
  Configure a load balancer to manage traffic with sticky sessions for consistent user experiences.

- [v2.4.0: Enable HTTPS](v2.5.0-enable-https.md)  
  Secure your WordPress site with HTTPS using certificates.

- [v2.5.0: Add a Standby Database](v2.6.0-standby-database.md)  
  Set up a standby database for high availability and disaster recovery.

---

## How to Navigate This Documentation

- Each version is designed to build upon the previous one, allowing you to implement features incrementally.
- Click on the links above to explore detailed instructions for each version.

---

Happy building! 🚀
