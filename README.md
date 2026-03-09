# Bearer Docker Scan

A project for scanning code using the Bearer security and privacy scanner.

## Overview

This project uses the Bearer scanner to analyze code for security and privacy issues. The scanner runs in a Docker container and analyzes code in the specified directories.

## Requirements

- Docker and Docker Compose
- Write access to the directories you want to scan

## Usage

To run the Bearer scanner, use the following command:

```bash
docker compose up -d
```

Or, if you want to run the scan immediately, you can use the following command:

```bash
docker compose run bearer scan /tmp/scan/<path-to-code> --debug
```

This will start the Bearer container and scan the code located at the path specified in your `.env` file, which is mounted to `/tmp/scan` inside the container.

### Report

To view the scan report, you can run it with the following tag:

```bash
docker compose run bearer scan /tmp/scan/<path-to-code> --debug --report security --output /tmp/scan/bearer-report.json
```

## Configuration

### Docker Compose Configuration

The configuration is defined in the `docker-compose.yml` file:

- The scanner uses the `bearer/bearer:latest-amd64` image
- The scanner runs on the `linux/amd64` platform
- Your local code directory is mounted to `/tmp/scan` inside the container

### Environment Variables

The project uses environment variables defined in a `.env` file:

- `HOST_CODE_PATH`: The path to the code directory on your local machine that should be scanned

You can customize these variables by editing the `.env` file.

## Additional Resources

- [Bearer Documentation](https://docs.bearer.com/)
- [Bearer GitHub Repository](https://github.com/bearer/bearer) 