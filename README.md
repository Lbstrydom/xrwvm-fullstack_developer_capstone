# Best Cars Dealership Review Portal

Capstone project for the IBM Full-Stack Software Developer Professional Certificate.

A national car dealership review platform where customers can browse dealer branches
across the United States, read and post reviews, and see sentiment analysis on those
reviews. Built as a Django application with a React front end, an Express/MongoDB
backend service for dealers and reviews, and a Flask/NLTK sentiment analysis
microservice, containerized with Docker and deployable to Kubernetes.

## Stack

- **Django** — user auth, car make/model data, proxy views to the backend services
- **React** — login, registration, dealer listing, dealer detail/reviews, review submission
- **Express + MongoDB** — dealer and review data, dockerized
- **Flask + NLTK (VADER)** — sentiment analysis microservice
- **Docker / Kubernetes** — containerized deployment

See `submission/SUBMISSION.md` for the full project tracker across all capstone modules.
