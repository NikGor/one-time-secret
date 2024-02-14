![CI/CD Status](https://github.com/NikGor/one-time-secret/actions/workflows/status.yml/badge.svg)

# One-Time Secret Service

🔒 This is a simple HTTP service for generating one-time secrets similar to [onetimesecret.com](https://onetimesecret.com/).

## Introduction

This service allows users to create secrets, set a passphrase for their retrieval, and generate a unique key to access the secret. The service provides a JSON API and does not include a UI.

## Technologies Used

- FastAPI
- Docker
- MongoDB
- pytest

## Installation and Setup

To run the service, make sure you have Docker and Docker Compose installed on your system. Then, follow these steps:

1. Clone this repository:

```bash
git clone <repository_url>
```

2. Navigate to the project directory:

```bash
cd <project_directory>
```

3. Build and start the Docker containers:

```bash
docker-compose up --build
```

4. The service should now be running and accessible at `http://localhost:8000`.

## API Endpoints

### Generate Secret

- **URL:** `/generate`
- **Method:** `POST`
- **Request Body:**
  - `secret`: The secret message to be stored.
  - `passphrase`: The passphrase required to retrieve the secret.
- **Response:** Returns a unique `secret_key` which can be used to retrieve the secret.

### Retrieve Secret

- **URL:** `/secrets/{secret_key}`
- **Method:** `GET`
- **Parameters:**
  - `secret_key`: The unique key generated during secret creation.
- **Request Header:**
  - `passphrase`: The passphrase provided during secret creation.
- **Response:** Returns the secret message if the correct passphrase is provided.

## Running Tests

To run the tests, execute the following command:

```bash
make test
```

## Advanced Features

- **Asynchronous Processing:** The service can be modified to handle requests asynchronously for improved performance.
- **External Storage:** Data storage can be implemented using an external storage solution like MongoDB.
- **Encryption:** Implement encryption for storing secrets and passphrases securely.
- **Time-To-Live (TTL):** Implement TTL indexes to automatically delete secrets after a certain period.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request with any improvements or additional features.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
