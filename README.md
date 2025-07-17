# Signature API

This is a simple Node.js API that generates a digital signature using a private key. It's designed to respond with a Base64-encoded signature for a given string of data. This can be used in tools like Postman to sign payloads or headers.

## Features

- Accepts a POST request with a JSON body containing `data`
- Signs the `data` using SHA-256 and a PEM-formatted private key
- Responds with the Base64-encoded digital signature
- Rejects all non-POST requests

## Requirements

- Node.js >= 14
- A private key in PEM format (`private_key.pem`) in the project root

## File Structure

```
project-root/
│
├── index-exp.js        # Main Express server
├── private_key.pem     # Your RSA private key (must be generated separately)
├── package.json        # Node.js dependencies and scripts
└── README.md           # Project documentation
```

## Getting Started

### 1. Install Dependencies

```bash
npm install
```

### 2. Add Your Private Key

Place your PEM-formatted RSA private key in the root of the project and name it `private_key.pem`.

You can generate one with:

```bash
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048
```

### 3. Start the Server

```bash
npm start
```

The server will run on [http://localhost:3001](http://localhost:3001)

## Usage Example (via Postman or curl)

### Request

- **Method**: `POST`
- **URL**: `http://localhost:3001/`
- **Headers**: `Content-Type: application/json`
- **Body**:

```json
{
  "data": "string-to-sign"
}
```

### Response

```json
{
  "signature": "<Base64-encoded-signature>"
}
```

## Unsupported Methods

All methods other than `POST` will return a 405 error with a proper message.

## License

MIT – Use freely.