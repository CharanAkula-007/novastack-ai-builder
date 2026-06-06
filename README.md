# Novastack-ai-builder


Novastack is an AI-powered web app builder that turns plain-English prompts into working web app code. The project includes a React + Vite frontend and an Express + MongoDB backend that connects to Gemini for code generation.

## What It Does

- Lets users sign up, log in, and manage projects
- Creates AI-generated web app code from chat-style prompts
- Shows a live preview and editable code view
- Supports renaming, saving, and deleting projects
- Lets users download generated code as an HTML file

## Tech Stack

- Frontend: React, Vite, React Router, Axios, js-cookie
- Backend: Node.js, Express, MongoDB, Mongoose
- AI: Google Gemini via `@google/genai`

## Project Structure

```text
client/   React app
server/   Express API
```

## Prerequisites

- Node.js 18 or later
- npm
- MongoDB connection string
- Gemini API key

## Setup

### 1. Install dependencies

From the project root, install each side separately:

```bash
cd client
npm install

cd ../server
npm install
```

### 2. Configure environment variables

Create a `.env` file inside `server/` with the following values:

```env
PORT=5000
CLIENT_URL=http://localhost:5173
MONGODB_URI=your_mongodb_connection_string
GEMINI_API_KEY=your_gemini_api_key
JWT_SECRET=your_jwt_secret
NODE_ENV=development
```

The frontend points to `http://localhost:5000/api` in `client/src/services/api.js`, so keep the backend running on that port unless you change the code.

## Run the App

### Start the backend

```bash
cd server
npm run dev
```

### Start the frontend

```bash
cd client
npm run dev
```

Then open the Vite URL shown in the terminal, usually `http://localhost:5173`.

## Available Scripts

### Client

- `npm run dev` - start the Vite development server
- `npm run build` - build the production bundle
- `npm run preview` - preview the production build locally

### Server

- `npm run start` - start the Express server
- `npm run dev` - start the Express server with file watching

## API Overview

All backend routes are mounted under `/api`.

### Auth

- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/auth/me`
- `POST /api/auth/logout`

### Projects

- `GET /api/projects`
- `POST /api/projects`
- `GET /api/projects/:id`
- `PUT /api/projects/:id`
- `DELETE /api/projects/:id`

### Generation

- `POST /api/generate/:projectId`

## How It Works

1. A user creates or opens a project from the dashboard.
2. The builder page sends prompts to the backend generation endpoint.
3. The backend uses Gemini to produce updated code and chat responses.
4. The frontend renders the result in preview and code tabs.

## Notes

- The backend expects MongoDB to be available before startup.
- Authentication is token-based and the frontend stores the token in cookies.
- Generated output is optimized for quick previewing and iteration.

## License

This project is currently published under the license declared in `server/package.json`.
