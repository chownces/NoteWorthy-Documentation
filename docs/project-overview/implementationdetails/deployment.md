# Implementation

### Deployment
This project is deployed on the following cloud providers:

- Frontend: Vercel
- Backend: Heroku
- Database: MongoDB Atlas

#### Vercel
Vercel has free hosting for personal projects and CD that is easy to set up, which suited our needs.

#### Heroku
Heroku's generous free hosting plan and easy CD setup satisfied our need for a PaaS to host our backend. However, it does come with downsides
such as the instance shutting down after 30 minutes of inactivity. This means that there will be 'cold starts' in our application after periods
of inactivity resulting initial lag time when accessing the backend, which is okay at the moment as this project is not deployed for production use.

#### MongoDB Atlas
MongoDB's SaaS database clusters has a generous free tier which suited our deployment needs for showcasing our project. It is also easy and
intuitive to set up.