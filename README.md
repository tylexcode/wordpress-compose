# WordPress Local Development with Docker Compose

This project sets up a local WordPress development environment using Docker Compose. It includes WordPress, MySQL, and Nginx services, with customizable configurations via a `.env` file.

## Prerequisites

- [Docker](https://www.docker.com/) installed on your machine.
- [Docker Compose](https://docs.docker.com/compose/) installed.
- Add the following entry to your `/etc/hosts` file:
  ```
  127.0.0.1 dev.wordpress.local
  ```

## Project Structure

```
.
├── docker-compose.yml       # Docker Compose configuration
├── .env                     # Environment variables for configuration
├── nginx/
│   └── default.conf         # Nginx configuration
├── config/
│   └── php.ini              # Custom PHP configuration
├── wordpress/               # WordPress files (auto-generated)
└── README.md                # Project documentation
```

## Configuration

### `.env` File
The `.env` file contains environment variables for database configuration:

```properties
# Database configuration
DB_NAME=<wordpress_db_name>
DB_USER=<wordpress_user>
DB_ROOT_PASSWORD=<root_password>
```

You can modify these values to suit your needs.

### Nginx Configuration
The `nginx/default.conf` file defines the virtual domain (`dev.wordpress.local`) and other server settings. You can customize it as needed.

### PHP Configuration
The `config/php.ini` file allows you to customize PHP settings such as `upload_max_filesize`, `post_max_size`, `max_execution_time`, and `memory_limit`.

## Usage

### 1. Build and Start the Containers
Run the following command to start the services:
```bash
docker-compose up -d
```

### 2. Access WordPress
Open your browser and navigate to:
```
http://dev.wordpress.local
```

### 4. Stop the Containers
To stop the containers, run:
```bash
docker-compose down
```

### 4. Restart the Containers
To restart the containers after making changes:
```bash
docker-compose restart
```

### 5. Access MySQL from the terminal
```
mysql -h 127.0.0.1 -P 3306 -u root -p
```

## Logs and Debugging

- View logs for all services:
  ```bash
  docker-compose logs -f
  ```
- View logs for a specific service (e.g., `wordpress`):
  ```bash
  docker-compose logs -f wordpress
  ```

## Customization

- **Database**: Modify the `.env` file to change database credentials.
- **Nginx**: Edit `nginx/default.conf` to customize the server configuration.
- **PHP**: Update `config/php.ini` to adjust PHP settings.

## Troubleshooting

- Ensure the `dev.wordpress.local` domain is added to your `/etc/hosts` file.
- Check container logs for errors:
  ```bash
  docker-compose logs
  ```
- Verify that Docker and Docker Compose are installed and running.

## License

This project is licensed under the MIT License.
