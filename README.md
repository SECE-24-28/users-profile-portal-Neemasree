# Users Profile Portal

A full-stack web application for managing student profiles, built with Next.js, GraphQL, Prisma, and PostgreSQL.

## Features

- User authentication (Register & Login) with JWT and bcrypt
- GraphQL API with Apollo Server
- Student profile management — add, view, update, delete
- Profile image upload support
- Protected routes (token-based)
- PostgreSQL database via Prisma ORM

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 16, React 19, Tailwind CSS |
| API | GraphQL (Apollo Server) |
| Auth | JWT, bcryptjs |
| ORM | Prisma |
| Database | PostgreSQL |
| File Upload | Multer |
| Language | TypeScript |

## Project Structure

```
my-app/
├── app/
│   ├── api/
│   │   ├── graphql/        # Apollo GraphQL API route
│   │   └── upload/         # File upload route
│   ├── login/              # Login page
│   ├── register/           # Register page
│   ├── students/           # Students dashboard page
│   └── page.tsx            # Home page
├── graphql/
│   ├── schema.ts           # GraphQL type definitions
│   └── resolvers.ts        # GraphQL resolvers
├── lib/
│   ├── auth.ts             # JWT auth helpers
│   └── prisma.ts           # Prisma client instance
├── prisma/
│   ├── schema.prisma       # Database schema
│   └── migrations/         # Migration history
└── public/
    └── uploads/            # Uploaded profile images
```

## Database Schema

**User** — `id`, `name`, `email`, `password`, `createdAt`

**Student** — `id`, `name`, `email`, `department`, `imageUrl`, `createdAt`

## Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL database

### 1. Clone the repository

```bash
git clone https://github.com/SECE-24-28/users-profile-portal-Neemasree.git
cd users-profile-portal-Neemasree/my-app
```

### 2. Install dependencies

```bash
npm install
```

### 3. Set up environment variables

Create a `.env` file in the `my-app` directory:

```env
DATABASE_URL="postgresql://<user>:<password>@<host>:<port>/<database>"
JWT_SECRET="your_jwt_secret_key"
```

### 4. Run database migrations

```bash
npx prisma migrate deploy
```

### 5. Start the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## GraphQL API

The GraphQL endpoint is available at `/api/graphql`.

### Mutations

```graphql
# Register a new user
mutation {
  register(name: "John", email: "john@example.com", password: "secret")
}

# Login
mutation {
  login(email: "john@example.com", password: "secret")
}

# Add a student
mutation {
  addStudent(name: "Jane", email: "jane@example.com", department: "CSE")
}

# Update a student
mutation {
  updateStudent(id: "1", name: "Jane Doe", department: "IT")
}

# Delete a student
mutation {
  deleteStudent(id: "1")
}
```

### Queries

```graphql
# Get all students
query {
  students {
    id
    name
    email
    department
    imageUrl
  }
}
```

## Scripts

```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run start    # Start production server
npm run lint     # Run ESLint
```
