# WordPress Docker Setup

This repository provides step-by-step guidance on setting up a WordPress environment with Docker. From a basic setup to advanced configurations like load balancing, HTTPS, and monitoring, this documentation helps you build and manage a robust WordPress infrastructure.

## Features

- **Versioned Setup**: Follow incremental improvements from basic setup to advanced features.
- **Docker Networking**: Secure your environment with public and private networks.
- **Backup and Restore**: Ensure data safety with comprehensive backup functionality.
- **Load Balancing**: Scale your application with round-robin DNS and sticky sessions.
- **HTTPS**: Secure your site with SSL certificates.
- **Monitoring**: Gain insights into container health and performance.

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. Navigate to the desired version in the [documentation](docs/index.md) and follow the instructions.

3. Start your Docker setup:
   ```bash
   docker-compose up -d
   ```

## Documentation

Detailed step-by-step instructions for each version are available in the [documentation](docs/index.md).

### Quick Links
- [v1.0.0: Basic Docker Compose Setup](docs/v1.0.0-basic-docker-compose.md)
- [v1.1.0: Manage Credentials Outside Compose File](docs/v1.1.0-manage-credentials.md)
- [v1.2.0: Backup and Restore Functionality](docs/v1.2.0-backup-restore.md)
- [v2.0.0: Create Public and Private Networks](docs/v2.0.0-public-private-network.md)
- [v2.1.0: Add Monitoring](docs/v2.1.0-add-monitoring.md)
- [v2.2.0: Add Web Containers with DNS Round-Robin](v2.2.0-web-dns-round-robin.md)
- [v2.3.0: Implement a Load Balancer with Sticky Sessions](v2.3.0-load-balancer-sticky-sessions.md)
- [v2.4.0: Enable HTTPS](v2.4.0-enable-https.md)  
- [v2.5.0: Add a Standby Database](v2.5.0-standby-database.md)

---

## Contribution

Contributions are welcome! Feel free to submit issues or pull requests to enhance this project.

## License

This project is licensed under the [MIT License](LICENSE).
