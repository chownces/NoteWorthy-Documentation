# Implementation Details

### Why these technologies?
#### Frontend
##### ReactJS
We settled with *ReactJS* as the library of choice in implementing our frontend as it is an industry standard for building
web applications today. This allows us to learn skills relevant to the industry, and build a level of proficiency and
familiarity in this library and its ecosystem, before moving on to bigger projects in the future.

#### Backend
##### Express
For the backend, we chose to use *Express* as it is a commonly used backend framework for small to medium projects. Besides,
the frontend was already written in TypeScript, and having prior experience with JavaScript syntax in *CS1101S Programming Methodology*
would allow for a lower initial learning curve.

##### GraphQL
We chose *GraphQL* over the traditional *RESTful API* for this project for <u>2 main reasons</u>:

1. *GraphQL* is gaining lots of traction in the industry and amongst big name companies such as Airbnb and GitHub!
1. Allows us to send queries to get the exact data we need without having to work with rigid server-defined endpoints.

    - This is crucial as our notetaking app requires slightly different variations of data from the backend for different pages.
    - This also means less work when implementing the API as we do not need multiple endpoints with specific shapes, while allowing the
frontend to only query the data it needs!

##### MongoDB
As we are working with dynamically structured data, using a document NoSQL database like *MongoDB* is a no-brainer. Also, it is widely
documented and well-integrated with *NodeJS* via libraries such as *Mongoose*. Deployment is also made easy with SaaS such as *MonggoDB Atlas*.

#### Deployment
##### Vercel
Vercel has free hosting for personal projects and CI that is easy to set up, which suited our needs.

##### Heroku
Heroku's generous free hosting plan and easy CI setup satisfied our need for a PaaS to host our backend. However, it does come with downsides
such as the instance shutting down after 30 minutes of inactivity. This means that there will be 'cold starts' in our application after periods
of inactivity resulting initial lag time when accessing the backend, which is okay at the moment as this project is not deployed for production use.

##### MongoDB Atlas
MongoDB's SaaS database clusters has a generous free tier which suited our deployment needs for showcasing our project. It is also easy and
intuitive to set up.