# Google Books Search

## Description

A full-stack MERN application that allows users to search for books via the Google Books API. Users can create an account, search for books, and save their favorite books to their profile. The application uses GraphQL API built with Apollo Server and Client, replacing the RESTful API architecture.

## Table of Contents

- [Google Books Search](#google-books-search)
  - [Description](#description)
  - [Table of Contents](#table-of-contents)
  - [Features](#features)
  - [Technologies Used](#technologies-used)
    - [Backend](#backend)
    - [Frontend](#frontend)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Project Structure](#project-structure)
  - [API References](#api-references)
    - [GraphQL Queries](#graphql-queries)
    - [GraphQL Mutations](#graphql-mutations)
  - [Authentication](#authentication)
  - [Contributing](#contributing)
  - [License](#license)
  - [Questions](#questions)
  - [Screenshots](#screenshots)

## Features

- User authentication (signup/login)
- Book search using Google Books API
- Save books to user profile
- View saved books
- Remove books from saved list
- Responsive design using React Bootstrap
- GraphQL API with Apollo Server
- JWT authentication
- MongoDB database with Mongoose ODM

## Technologies Used

### Backend
- Node.js
- Express.js
- MongoDB
- Mongoose
- Apollo Server
- GraphQL
- JWT Authentication
- TypeScript
- bcrypt

### Frontend
- React
- Apollo Client
- React Bootstrap
- React Router DOM
- TypeScript
- JWT Decode
- Vite

## Installation

1. Clone the repository:
```bash
git clone [repository-url]
```

2. Install dependencies for the root, server, and client:
```bash
npm install
```

3. Create a `.env` file in the server directory with the following variables:
```
MONGODB_URI='mongodb://127.0.0.1:27017/googlebooks'
JWT_SECRET_KEY='your-secret-key'
```

4. Start the development server:
```bash
npm run dev
```

## Usage

1. Visit `http://localhost:3000` in your browser
2. Create an account or log in
3. Search for books using the search bar
4. Click "Save this Book!" to save books to your profile
5. View saved books by clicking "See Your Books" in the navigation
6. Remove books from your saved list using the "Delete this Book!" button

## Project Structure

```
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── components/    # React components
│   │   ├── pages/        # Page components
│   │   ├── utils/        # Utility functions
│   │   └── models/       # TypeScript interfaces
│   └── ...
├── server/                # Backend Node.js application
│   ├── src/
│   │   ├── config/       # Database configuration
│   │   ├── models/       # Mongoose models
│   │   ├── schemas/      # GraphQL schemas
│   │   └── services/     # Authentication services
│   └── ...
└── package.json
```

## API References

### GraphQL Queries

```graphql
query me {
  me {
    _id
    username
    email
    bookCount
    savedBooks {
      bookId
      authors
      description
      title
      image
      link
    }
  }
}
```

### GraphQL Mutations

```graphql
mutation login($email: String!, $password: String!) {
  login(email: $email, password: $password) {
    token
    user {
      _id
      username
    }
  }
}

mutation addUser($username: String!, $email: String!, $password: String!) {
  addUser(username: $username, email: $email, password: $password) {
    token
    user {
      _id
      username
    }
  }
}

mutation saveBook($bookData: BookInput!) {
  saveBook(bookData: $bookData) {
    _id
    username
    savedBooks {
      bookId
      authors
      description
      title
      image
      link
    }
  }
}

mutation removeBook($bookId: String!) {
  removeBook(bookId: $bookId) {
    _id
    username
    savedBooks {
      bookId
      title
    }
  }
}
```

## Authentication

The application uses JSON Web Tokens (JWT) for authentication. Tokens are stored in localStorage and included in the Authorization header for GraphQL requests. The token expires after 2 hours.

## Contributing

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Submit a pull request

## License

This project is licensed under the ISC License.



## Screenshots

![Screenshot 1](/assets/query.png)
![Screenshot 2](/assets/user.png)
