# Getting Started
The instructions for backend setup can be found on this page.

## Backend
#### MongoDB Database Setup
1. Install and start MongoDB by following the instructions on their [installation site](https://docs.mongodb.com/manual/installation/).

#### Express Server Setup
1. Install a stable version of NodeJS. The LTS or current version should work fine.
1. Clone [this repository](https://github.com/chownces/NoteWorthy-API), and navigate to it using `cd` in your command line.
1. Run `yarn install` to install the dependencies.
1. Copy the `.env.example` file to `.env`, and configure the environment variables (more details [below](#environment-configuration)).
1. Run `yarn start` to start the local server at `localhost:4300`.
1. Navigate to `localhost:4300/graphql` to interact with the GraphQL Console.

#### Environment Configuration
- `MONGODB_URI`: The URL to your MongoDB database. By default, the local development database can be
found at `mongodb://localhost:27017/your_database_name` (replace `your_database_name` with the
actual name of your database).
- `MONGODB_USERNAME`: The username of your MongoDB account (*optional* for local development).
- `MONGODB_PASSWORD`: The password to your MongoDB account (*optional* for local development).
- `CORS_ORIGIN`: The URL of your frontend. Use `localhost:3000` for local development.
- `SESSION_SECRET`: A randomly generated string for initializing *express-session*.

#### Testing
- Please format your code with `yarn format` and run the test suite via `yarn test` before pushing and issuing a PR.