# Destinize Backend API

A backend API for the Destinize travel application, managing users, administrators, travel packages, and reservations.

![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/Express-404D59?style=for-the-badge&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=json-web-tokens&logoColor=white)

## Description

This project provides a robust backend API for the Destinize travel platform. It handles user authentication, admin management, travel package listings, image uploads, and reservation processing. The API is built using Node.js and Express.js, with a MySQL database for data storage.

## Features

*   **User and Admin Management**: Separate endpoints for managing user and administrator accounts, including authentication.
*   **Travel Package Management**: Create, read, update, and delete travel packages with associated images.
*   **Reservation System**: Users can make reservations, and administrators can manage them. Includes payment status updates.
*   **Image Uploads**: Supports uploading images for travel packages and proof of payment for reservations.
*   **Token-Based Authentication**: Uses JSON Web Tokens (JWT) for securing API endpoints.

## Tech Stack

*   **Runtime**: Node.js
*   **Framework**: Express.js
*   **Database**: MySQL (using `mysql2` package)
*   **Authentication**: JSON Web Tokens (JWT)
*   **File Uploads**: Multer
*   **Environment Variables**: dotenv
*   **Cross-Origin Resource Sharing**: CORS

## Installation

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/fadlananshari/fadlananshari-backend-destinize.git
    cd fadlananshari-backend-destinize
    ```

2.  **Install dependencies**:
    ```bash
    npm install
    ```

3.  **Set up environment variables**:
    Create a `.env` file in the root directory and populate it with your database credentials and port. Use the `.env.example` file as a template:
    ```
    PORT=
    DB_HOST=
    DB_USERNAME=
    DB_PASSWORD=
    DB_NAME=
    ```

4.  **Database Setup**:
    Ensure you have a MySQL database running and create the necessary tables based on the models defined in the `src/models` directory.

5.  **Run the server**:
    ```bash
    npm start
    ```
    Or for development with automatic restarts:
    ```bash
    npm run dev
    ```

## API Endpoints

All API endpoints are prefixed with `/api/v1`.

### Authentication (`/auth`)

*   `POST /api/v1/login`: Admin login.
*   `POST /api/v1/user/login`: User login (creates user if not exists).
*   `GET /api/v1/decode-token/:token`: Decodes a JWT.

### Users (`/users`)

*   `POST /api/v1/user`: Create a new user.
*   `GET /api/v1/users`: Get all users.
*   `GET /api/v1/user/:idUser`: Get a user by ID.
*   `POST /api/v1/user/token-check`: Checks the validity of a user token.

### Admins (`/admins`)

*   `POST /api/v1/admin`: Create a new admin.
*   `GET /api/v1/admins`: Get all admins.
*   `GET /api/v1/admin/:idAdmin`: Get an admin by ID.
*   `PATCH /api/v1/admin/:idAdmin`: Update an admin.
*   `DELETE /api/v1/admin/:idAdmin`: Delete an admin.
*   `POST /api/v1/admin/token-check`: Checks the validity of an admin token.

### Travel Packages (`/paket-wisata`)

*   `GET /api/v1/paket-wisata`: Get all travel packages.
*   `GET /api/v1/paket-wisata/:id`: Get a travel package by ID.
*   `POST /api/v1/Paket-wisata`: Create a new travel package.
*   `PATCH /api/v1/Paket-wisata/tambah-foto/:id`: Upload a photo for a travel package.
*   `PATCH /api/v1/paket-wisata/:id`: Update a travel package.
*   `DELETE /api/v1/paket-wisata/:id`: Delete a travel package.
*   `DELETE /api/v1/paket-wisata/:id/file/:filename`: Delete a travel package photo (from file system and potentially DB).

### Gallery (`/galeri`)

*   `GET /api/v1/galeri`: Get all gallery photos.
*   `GET /api/v1/galeri/:id_paket/id-paket`: Get gallery photos by package ID.
*   `POST /api/v1/galeri/:id`: Upload a new photo to the gallery for a specific package.
*   `DELETE /api/v1/galeri/:id/file/:filename`: Delete a gallery photo (from file system and potentially DB).

### Reservations (`/reservasi`)

*   `GET /api/v1/reservasi`: Get all reservations.
*   `GET /api/v1/reservasi/:id`: Get a reservation by ID.
*   `GET /api/v1/reservasi/user/:id_user`: Get reservations for a specific user.
*   `POST /api/v1/reservasi/:id_user/:id_paket`: Create a new reservation.
*   `PATCH /api/v1/reservasi/bukti/:id`: Upload proof of payment for a reservation.
*   `PATCH /api/v1/reservasi/:id`: Update a reservation.
*   `PATCH /api/v1/reservasi/ubah-status/:id`: Update the payment status of a reservation.
*   `DELETE /api/v1/reservasi/:id`: Delete a reservation.

## Project Structure

fadlananshari-backend-destinize/ ├── index.js # Main server entry point ├── package.json # Project dependencies and scripts ├── vercel.json # Vercel deployment configuration ├── .env.example # Example environment variables ├── public/ # Static assets │ └── images/ # Stored uploaded images └── src/ ├── config/ # Database configuration │ └── database.js ├── controller/ # Request handlers and business logic │ ├── admins.js │ ├── auth.js │ ├── galeri.js │ ├── jwtToken.js # JWT generation and verification │ ├── paketWisata.js │ ├── reservasi.js │ └── users.js ├── middleware/ # Request processing middleware │ ├── logs.js # Request logging │ └── multer.js # File upload handling ├── models/ # Database interactions (SQL queries) │ ├── admins.js │ ├── galeri.js │ ├── paketWisata.js │ ├── reservasi.js │ └── users.js └── routes/ # API route definitions ├── admins.js ├── auth.js ├── galeri.js ├── index.js # Main router ├── paketWisata.js ├── reservasi.js └── users.js


## Contributing

Contributions are welcome! Please follow these steps:

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature-name`).
3.  Make your changes.
4.  Commit your changes (`git commit -am 'Add some feature'`).
5.  Push to the branch (`git push origin feature/your-feature-name`).
6.  Open a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
