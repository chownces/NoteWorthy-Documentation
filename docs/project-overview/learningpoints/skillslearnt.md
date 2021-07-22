# Skills Learnt
As this was the first authenticated web project we have ever done
from scratch, we had to pick up many technologies and knowledge along 
the way. This page seeks to summarise the skills that we have learnt
since embarking on this project.

For the rationale behind choosing this tech stack, please refer to the
earlier page [here](/noteworthy-documentation/project-overview/implementationdetails/whytechstack/).

<hr/>

### ReactJS
As the main library for our frontend, we have gained a better
understanding of React Hooks and the React Lifecycle when implementing
the *draggable* and *contenteditable div* UI logic for our notetaking app.
We also gained a deeper appreciation of the packages available in the
React ecosystem, and where React excels at *(and hence its popularity)*.

<u>Learnt</u>: the latest *React Hooks* standard, the *React Lifecycle*,
standard React Hooks such as *useState*, *useRef*, *useCallback*,
*useMemo* and when to use them or create custom hooks

<hr/>

### GraphQL
This was our first time using GraphQL in a project, and it was a
refreshing take on the whole API call workflow! We really enjoyed
using it *(Apollo's implementation of GraphQL)* and would definitely
consider using it again in future projects as opposed to the traditional
RESTful API.

<u>We really liked:</u>

1. The inbuilt **intelligent and normalized cache system** without any
additional configuration
    - Knows when to refetch data and when to return cached values
    - API which provides finetuned controls for modifying the cache
      during GraphQL queries or mutations
    - Relieving ourselves of the need to implement our own frontend
      store with something like Redux, and all the boilerplate code
      that comes with it...

1. No routing headaches in the backend
    - GraphQL only has a single endpoint through which all queries and
      mutations are made!

1. No need to work with rigid server-defined endpoints (of RESTful APIs)
    - We can query for a subset of the data returned from a GraphQL
      query or mutation → allows us to get the exact data we need without
      needing to define new queries or mutations, which is not possible
      with the RESTful API
    - Thus less changes needed in both frontend and backend between
      software iterations

1. Built-in option for **Optimistic Response**, which follows the
  *Optimistic UI pattern*, and allows for 'snappier' UI and better
  user experience (crucial to our notetaking app which autosaves
  periodically when there are changes)

    > Optimistic UI is a pattern that you can use to simulate the results of a mutation and update the UI even before receiving a response from the server. Once the response is received from the server, the optimistic result is thrown away and replaced with the actual result.

    > Optimistic UI provides an easy way to make your UI respond much faster, while ensuring that the data becomes consistent with the actual response when it arrives.
    >
    > <div style="text-align: right">*~ Explanation of Optimistic UI by Apollo*</div>

1. Built-in GraphQL Playground
    - Allows us to run manual queries or mutations to our GraphQL backend
      through a GUI without something like Postman or a working frontend
    - Provides a quick sanity check when implementing our GraphQL
      resolvers

<u>What we didn't like:</u>

1. GraphQL is verbose in its own way
    - The [GraphQL schema](https://graphql.org/learn/schema/) needs to be
      defined in both the backend, and in every single GraphQL query or
      mutation called from the frontend (to specify what data and type
      to return)
    - This can mean a dozen or so lines per query or mutation, as
      opposed to the one-liner to a RESTful endpoint
    - Worse still, this schema is written as a JavaScript string and is
      painful to read in a code editor...

1. Sparse documentation and changing specifications
    - GraphQL is still rapidly developing, leading to less robust
      documentation and changing specifications
    - As it is relatively newer, there are also less forum questions
      and answers available

<u>Bottomline</u>:

- Whether to use GraphQL or the RESTful API standard really boils down
  to the tradeoffs one is willing to make, as discussed above
- Through this project, we can really see the benefits that GraphQL
  brings to the table, and why many big companies are shifting over to
  this new paradigm for API development

<hr/>

### MongoDB
This was also our first time using a NoSQL database like MongoDB. Thankfully,
with great JavaScript wrapper libraries such as `mongoose`, we were able to
get up to speed quickly and implement the persistence in our notetaking app.

<hr/>

### Deployment
This project opened our eyes to the world of DevOps and CI/CD, and we learnt
a great deal about deployment to cloud providers, which is widely used
today. We also managed to read up on the various types of cloud computing, such
as IaaS, PaaS and SaaS, and the pros and cons of each of these.

We also learnt about the handling of secrets and environment variables, and never
to expose them in the actual codebase.

Click [here](/noteworthy-documentation/project-overview/implementationdetails/deployment/)
for more information on the deployment of this project, and [here](/noteworthy-documentation/project-overview/implementationdetails/workflow/)
for more information on the CI/CD employed in this project.

<hr/>

### Authentication
This was also our first time implementing authentication for a web app.
During the learning process, we researched on the various types of authentication
methods that are used today, such as session cookies and OAuth with JSON
Web Tokens (JWTs). We also read up on and used `PassportJS` which is an
authentication library in JavaScript.

Due to time constraints, we ended up using a library `express-session` for
session cookie authentication, and implemented a simple password login (where
the passwords are hashed and stored on the backend - which is not really ideal
in a production scenario due to potential security concerns).

Given more time, we would have tried implementing the JWT auth flow with
3rd party OAuth providers, such as GitHub, Google or Facebook, or even use OpenID
connect.

<hr/>

### Documentation
We decided to use a *static site generator* for our project documentation,
as we can easily organize the content via markdown files. After looking around, we
settled on `mkdocs-material`, and learnt how to write markdown and deploy it to GitHub Pages.

<hr/>

### GitHub
We used Git as our code version control system, and hosted the remote repo on GitHub.
Through this project, we gained a deeper understanding of Git's functionality, such as
*branching*, *merging* and *rebasing*, and utilized the GitHub *pull request workflow* for
collaboration. This would enable us to collaborate more effectively in future projects
of larger scale.

We also made use of GitHub's Actions to run our CI checks.