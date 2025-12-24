# Squid Docker

Simple Docker Compose setup for running a Squid proxy with local config and HTTP auth.

## Repository layout
- `docker-compose.yml` — service definition for the Squid container  
- `passwd` — HTTP auth password file (htpasswd format)  
- `squid.conf` — Squid configuration file mounted into the container  
- `logs/` — directory where Squid writes logs (mounted volume)

## Prerequisites
- Docker Engine
- Docker Compose (or Docker CLI plugin: `docker compose`)

## Quick start
1. Start the service:
    ```bash
    docker compose up -d
    ```
2. Follow logs:
    ```bash
    docker compose logs -f squid
    ```
3. Restart after config changes:
    ```bash
    docker compose restart squid
    ```

## Config and auth
- Edit `squid.conf` to adjust Squid settings, then restart the container.
- Create or update the HTTP auth file using `htpasswd`. Example (bcrypt):
    ```bash
    # install apache2-utils or httpd-tools if needed
    htpasswd -B -c passwd username
    # omit -c to add/update additional users
    ```

## Notes
- Review `squid.conf` for access rules and logging.
- Ensure `passwd` and `logs/` have permissions writable by the container user.

## License
This project is licensed under the MIT License — see [LICENSE](./LICENSE) for details.