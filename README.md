# Docker Base Micro services

## Secrets

To manage sensitive information, you can use the `secrets` directory. Below are instructions and sample files for managing secrets:

### Instructions

1. **Create Secret Files**: Create text files in the `secrets` directory for each sensitive piece of information. For example:
   - `n8n_user.txt`: Contains the username for n8n.
   - `n8n_password.txt`: Contains the password for n8n.
   - `portainer_admin_password.txt`: Contains the admin password for Portainer.
   - `postgres_user.txt`: Contains the username for PostgreSQL database.
   - `postgres_password.txt`: Contains the password for PostgreSQL database.
   - `postgres_db.txt`: Contains the default database name for PostgreSQL.

2. **Accessing Secrets**: Ensure that your application can access these files securely. You may need to configure your Docker containers to mount the `secrets` directory.

### Generating Secure Passwords

You can generate secure, random passwords using the following terminal commands:

#### Using OpenSSL (Linux/macOS/Windows with OpenSSL installed)

```bash
# Generate a 32-character random password
openssl rand -base64 32

# Generate a 24-character random password
openssl rand -base64 24

# Generate a 16-character random password
openssl rand -base64 16
```

#### Using mkpasswd (Linux/macOS)

```bash
# Generate a hashed password (useful for system passwords)
mkpasswd -m sha-512

# Or generate a simple random password
tr -dc 'A-Za-z0-9!@#$%^&*' < /dev/urandom | head -c 32 ; echo
```

#### Using PowerShell (Windows)
Generate a 32-character random password
```powershell
$password = ([char[]]([char]33..[char]126) | Sort-Object {Get-Random}) -join '' | Select-Object -First 32; Write-Host $password
```

#### Using cmd.exe (Windows) with certutil

```cmd
# Generate a base64-encoded random string
certutil -encodehex -f C:\Windows\System32\drivers\etc\hosts - | find /v ":" | head -c 32
```

#### Quick one-liner for Python (if installed)

```python
python -c "import secrets; print(secrets.token_urlsafe(32))"
```

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

- **postgres_user.txt**

  ```
  postgres
  ```

- **postgres_password.txt**

  ```
  your_postgres_password
  ```

- **postgres_db.txt**

  ```
  postgres
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
