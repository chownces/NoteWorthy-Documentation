# Getting Started
The instructions for frontend setup can be found on this page.

## Frontend
#### ReactJS Setup
1. Install a stable version of NodeJS. The LTS or current version should work fine.
1. Clone [this repository](https://github.com/chownces/NoteWorthy), and navigate to it using `cd` in your command line.
1. Run `yarn install` to install the dependencies.
1. Copy the `.env.example` file to `.env`, and configure the environment variables (more details [below](#environment-configuration)).
1. Run `yarn start` to start the local server at `localhost:3000`.
1. Navigate to `localhost:3000` on your browser.

#### Environment Configuration

- `REACT_APP_BACKEND_URL`: Specify the URL of your backend. By default, the local development backend
can be found at `http://localhost:4300/graphql/`.

#### Testing
- Please format your code with `yarn format` and run the test suite via `yarn test` before pushing and issuing a PR.