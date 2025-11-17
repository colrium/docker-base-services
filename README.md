# Docker Base Micro services

## Secrets

To manage sensitive information, you can use the `secrets` directory. Below are instructions and sample files for managing secrets:

### Instructions

1. **Create Secret Files**: Create text files in the `secrets` directory for each sensitive piece of information. For example:
   - `n8n_user.txt`: Contains the username for n8n.
   - `n8n_password.txt`: Contains the password for n8n.
   - `portainer_admin_password.txt`: Contains the admin password for Portainer.

2. **Accessing Secrets**: Ensure that your application can access these files securely. You may need to configure your Docker containers to mount the `secrets` directory.

### Sample Secret Files

- **n8n_user.txt**

  ```
  your_username
  ```

- **n8n_password.txt**

  ```
  your_password
  ```

- **portainer_admin_password.txt**

  ```
  your_portainer_admin_password
  ```

Make sure to replace the placeholders with your actual sensitive information.


## Deployment

### Create network

```console
docker network create gateway
```

### Run

```console
docker-compose up -d
```
