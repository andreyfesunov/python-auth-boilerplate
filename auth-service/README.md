# Python Authentication Service Boilerplate

A robust authentication service boilerplate that provides JWT-based authentication capabilities and JWKS (JSON Web Key Set) endpoint for distributed systems.

## Features

- JWT-based authentication
- JWKS endpoint for public key distribution
- Secure key pair management
- Easy integration with other services
- Standardized authentication flows

## Getting Started

### Prerequisites

- Python 3.12+
- uv
- ansible

### Installation

1. Clone the repository
2. Create and activate virtual environment:
```bash
uv venv
source .venv/bin/activate  # For Unix
.venv\Scripts\activate     # For Windows
```
3. Install dependencies:
```bash
uv pip install -r requirements.txt
```
4. Set up pre-commit hooks:
```bash
pre-commit install
```

## Development

### Pre-commit Hooks

This project uses pre-commit hooks to ensure code quality. The hooks include:
- Code formatting with black
- Type checking with mypy

To run the hooks manually:
```bash
pre-commit run --all-files
```

## Deployment

The service is deployed using Ansible. Check the `ansible` directory for playbooks and configuration.

```bash
ansible-playbook -i inventory/hosts playbooks/deploy.yml
```

## Usage

### JWKS Endpoint

The service exposes a JWKS endpoint at `/jwks` which provides public keys for JWT verification by other services.

### Authentication Endpoints

- `POST /auth/login` - Login endpoint
- `POST /auth/refresh` - Token refresh endpoint
- `POST /auth/verify` - Token verification endpoint

## Configuration

Configuration can be done through environment variables or `.env` file:

```
JWT_SECRET_KEY=your-secret-key
JWT_ALGORITHM=RS256
TOKEN_EXPIRATION=3600
```

## Integration

Other services can verify JWTs by fetching public keys from the JWKS endpoint:

```
GET /jwks
```

## License

MIT
