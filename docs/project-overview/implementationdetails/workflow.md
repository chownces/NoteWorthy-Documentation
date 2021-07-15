# Implementation Details

### Workflow
#### Version Control
We used Git and GitHub as our code version control system. For collaboration, we used the pull request (PR) workflow to commit to
our `master` branch. This enables us to stay up to date with what our partner is working on, and also have an extra pair of eyes
on code quality.

#### Continuous Integration and Continuous Delivery (CI/CD)
We also decided to focus fairly heavily on learning the CI/CD side of DevOps in this project, as we found this knowledge to be
invaluable to future software projects that we will be working on. The following is a short summary of the CI/CD workflow we
have employed:

<u>Continuous Integration</u>

1. Pre-push checks
    - We used [*husky*](https://www.npmjs.com/package/husky) to run pre-push Git hooks that do code linting, formatting checks and run tests
      locally before allowing the commit to be pushed to our GitHub repository
    - This ensures that the code on GitHub is formatted and passing our tests before others review/ deploy it
1. GitHub Actions
    - We used GitHub workflow actions in our next step of CI to run the above checks again on GitHub's server to ensure everything is ok
    - This time, we also build the application to ensure that it is ready for deployment
1. GitHub Dependabot
    - GitHub's Dependabot was also set up to check for dependency updates in the packages we use for this project
    - This is extremely convenient as Dependabot automatically sets up PRs and runs our test suite whenever there are packages that can be
      updated

<u>Continuous Delivery</u>

1. Vercel
    - Vercel has a bot that is well integrated with GitHub, and was set up to automatically deploy our production branch with our production
      configuration
    - This streamlines our frontend deployment as all we have to do is just push to the production branch

1. Heroku
    - Heroku has a similar CD workflow as Vercel, and automatically deploys our production branch with our production configuration whenever
      there are changes
    - A post-build script is also ran when there are new database migration files

#### Database Migrations
We also spent some time working on database migrations as having working knowledge in this aspect will be useful in future software projects
that involve backend updates and database schema changes.

More specifically, we are using a package [*migrate-mongo*](https://www.npmjs.com/package/migrate-mongo) to write our migration files for
MongoDB. The migrations are ran automatically via a post-build script that we inserted as part of Heroku's CD.