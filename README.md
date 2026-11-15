# Bobajob website preview

Bobajob is a local community marketplace concept for suitable, short, one-off tasks. The initial launch area is Surrey, with possible UK expansion later.

## Current status

This repository contains a **front-end demonstration**, not a live marketplace. It is intentionally limited to sample data and in-browser interactions.

- Responsive homepage and navigation
- Example job cards, search and category/postcode filters
- Job details and job-posting form preview
- How-it-works and safety pages
- Teen, parent and adult dashboard previews
- Parent approval and three-person chat workflow explanations

## Run locally

Open `index.html` in a browser, or serve the folder with any static web server.

## Important limitations

There is currently no production authentication, database, persistent user data, messaging, payments, identity verification, or real job acceptance. Do not use this preview to arrange work or collect personal information. The sample jobs and prices are fictional.

The previous prototype's direct password storage and client-side database access have been removed. Do not add credentials, passwords, payment card data, service-role keys or personal information to this repository.

## Planned production architecture

- Next.js + TypeScript for the application
- Supabase Auth for secure authentication
- Supabase Postgres with Row Level Security for data access
- Supabase Realtime for participant-only job chats
- Private object storage for profile media
- A regulated marketplace payment provider, subject to legal/provider approval
- GitHub for version control and review
- Vercel or another suitable host for deployment

See [production-readiness.md](docs/production-readiness.md) before implementing live functionality.

## Development branch

The first implementation is on `bobajob-foundation`. Review it before merging into `main`.
