# Tesla X Delivery Giveaway

This repository is a scaffold for a multi-prize electric car giveaway site (13 prizes). It uses a Vite + React frontend and Supabase (Postgres + Edge Functions) for backend tasks like storing entries and picking winners. SendGrid is used for email notifications and Google reCAPTCHA for anti-bot protection.

This project is scaffolded with sensible defaults to get you started quickly. It deliberately uses placeholders for secrets — DO NOT commit real API keys.

Quick overview
- Frontend: Vite + React
- Backend: Supabase (Postgres tables + Edge Function to pick winners)
- Email: SendGrid (server-side)
- Hosting: Deploy frontend to Vercel; Supabase handles DB and Edge Functions

Contents
- /src — React app
- /supabase/db-schema.sql — SQL to run in Supabase to create tables
- /supabase/functions/pick-winners — Edge Function stub to select winners
- .env.example — environment variable examples

Important
- Keep SUPABASE_SERVICE_ROLE_KEY and SENDGRID_API_KEY secret. Use Vercel / Supabase dashboard to store them.

Next steps
1. Create a Supabase project
2. Run the SQL in /supabase/db-schema.sql in Supabase SQL editor
3. Set environment variables in Vercel & Supabase
4. Deploy frontend to Vercel and the function to Supabase Edge Functions

If you want, I can walk you through each step and help configure Supabase and Vercel.

Docker (local build & dev)

This project includes a Dockerfile (multi-stage) for building a production image and a docker-compose.yml for local development including a Postgres service (optional).

Build the production image and run it:

  docker build -t tesla-x-app:latest .
  docker run --rm -p 8080:80 tesla-x-app:latest

Open http://localhost:8080

Run using docker-compose (build + local Postgres dev DB):

  # create .env.local with the variables used by docker-compose, or set them in your shell
  docker-compose up --build

Stop:

  docker-compose down

Notes
- The Dockerfile performs a node-based build and serves the static /dist via nginx.
- The compose file is provided for local dev workflows. In production we recommend deploying the frontend to Vercel and using Supabase for the database and Edge Functions.

Security reminder: never commit your production secrets to source control. Use Vercel / Supabase secret managers.
