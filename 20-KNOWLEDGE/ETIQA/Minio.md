# MinIO Local Development Setup

  

This guide shows how to set up and run MinIO locally for development with the smile-aio project.

  

## Quick Start

  

### 1. Start MinIO Service

  

The project already includes MinIO in docker-compose.yml:

  

```bash

# Navigate to container directory

cd /Users/salehloke/Developer/smile-aio/container

  

# Start MinIO (and optionally other services)

docker-compose up minio -d

  

# Or start all services

docker-compose up -d

```

  

### 2. Access MinIO Console

  

- **MinIO Server**: http://localhost:9000 (for API access)

- **MinIO Console**: http://localhost:9001 (for web UI)

- **Username**: `etiqaadmin`

- **Password**: `Minio#2023`

  

### 3. Backend Configuration

  

Ensure your backend `.env` file has these variables:

  

```bash

# MinIO Configuration for Local Development

MINIO_ENDPOINT=localhost

MINIO_PORT=9000

MINIO_SSL=false

MINIO_ACCESS_KEY=etiqaadmin

MINIO_SECRET_KEY=Minio#2023

```

  

## Creating Required Buckets

  

### Method 1: Using MinIO Client (Recommended)

  

```bash

# Install MinIO client

brew install minio/stable/mc # macOS

# or

curl https://dl.min.io/client/mc/release/linux-amd64/mc -o mc && chmod +x mc # Linux

  

# Configure connection

mc alias set local http://localhost:9000 etiqaladmin 'Minio#2023'

  

# Create application buckets

mc mb local/enjoy-rewards-bucket

mc mb local/announcement-bucket

  

# Set public read policy for development

mc anonymous set public local/enjoy-rewards-bucket

mc anonymous set public local/announcement-bucket

  

# Verify buckets

mc ls local/

```

  

### Method 2: Using Web Console

  

1. Go to http://localhost:9001

2. Login with `etiqaladmin` / `Minio#2023`

3. Click "Buckets" → "Create Bucket"

4. Create:

- `enjoy-rewards-bucket`

- `announcement-bucket`

  

## Testing the Setup

  

### Test with Backend API

  

1. Start your backend application

2. Try uploading an image through the voucher image upload endpoints:

- `POST /portal-enjoy-rewards/rewards/voucher/upload-background-image`

- `POST /portal-enjoy-rewards/rewards/voucher/upload-logo-image`

  

### Test with Frontend

  

1. Start your frontend application

2. Navigate to the voucher details page

3. Try uploading images using the image upload components

  

## Troubleshooting

  

### MinIO Not Starting

```bash

# Check container logs

docker-compose logs minio

  

# Restart MinIO

docker-compose restart minio

```

  

### Connection Issues

- Verify MinIO is running: `docker-compose ps minio`

- Check environment variables in backend

- Ensure buckets exist and have proper permissions

  

### Upload Failures

- Check bucket permissions (should be public for development)

- Verify file types are supported (jpeg, jpg, png, svg, gif)

- Check file size limits

  

## Docker Compose Configuration

  

The project's docker-compose.yml includes:

  

```yaml

minio:

image: minio/minio

restart: always

ports:

- 9000:9000

- 9001:9001

environment:

MINIO_ROOT_USER: etiqaladmin

MINIO_ROOT_PASSWORD: Minio#2023

MINIO_ADDRESS: ':9000'

MINIO_CONSOLE_ADDRESS: ':9001'

command: minio server /data

volumes:

- minio_storage:/data

```

  

## Useful Commands

  

```bash

# Start only MinIO

docker-compose up minio -d

  

# Stop MinIO

docker-compose stop minio

  

# View MinIO logs

docker-compose logs -f minio

  

# Reset MinIO data

docker-compose down

docker volume rm container_minio_storage

docker-compose up minio -d

  

# List all buckets

mc ls local/

  

# Check bucket contents

mc ls local/enjoy-rewards-bucket/

  

# Remove a bucket

mc rb local/bucket-name --force

```

  

## Production vs Development

  

### Development (Local)

- Uses HTTP (no SSL)

- Simple credentials

- Public bucket policies for easy testing

- Data stored in Docker volume

  

### Production

- Uses HTTPS (SSL enabled)

- Strong credentials

- Restricted bucket policies

- Data stored in persistent storage

- Load balancing and high availability setup