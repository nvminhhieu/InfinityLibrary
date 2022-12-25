# Inifinity Library

An android app connecting users who want to exchange book on a marketplace platform.

User can list books they want to sell on the app, and also purchase from others.

[demo](https://user-images.githubusercontent.com/52330522/209464188-aaf34bb0-29ae-4ac6-9fbb-766e8a5bd19c.webm)

## Tech stack

### Frontend

- Expo
- React Native

### API Framework

- FastAPI

### Database

- Postgresql
- Redis
- Sqlalchemy (data modeling and querying)
- Pydantic (data schemas)
- Alembics (data migration)

### Containerization

- Docker
- Docker compose (development)
- Kubernetes (production)

### CI/CD

- Github Actions

### Deployment environment

- AWS EKS (Amazon Web Service Elastic Kubernetes Service)
- AWS ECR (private repository to store docker images)

### Others

- Ingress Nginx (https://kubernetes.github.io/ingress-nginx/)
- OpenAPI
- Makefile
- Bash
- Pylint, pep8
- Eslint

## How to install

### Development

The whole development workflow is powered by `docker` and `docker-compose`.
To run the application locally, only `docker` and `docker-compose` are required to be installed
In order to install `docker` and `docker-compose`. Please visit https://docs.docker.com/compose/install/

#### Usage

To start the application, make sure you have `npm` and `expo` installed

Then, navigate to `/client`:

```bash
npm i
npm start
```

To start the backend application using `docker-compose`

```bash
docker compose up --build
```
To stop the application, open new terminal and run command:
```bash
docker compose down
```
To run tests
```
pytest
```

**NOTE**: The app is currently running only on mock_data on the Client. To connect with the backend localhost server, find `env.ts`, change `LOCALHOST` to your localhost address.


### Production

The application is separated into two parts: front-end is a cross-platform mobile application powered by React Native, back-end is a FastAPI server running in Docker and Kubernetes environment.
Therefore, there are two deployment workflows for the application.

#### Frontend

The mobile application will be automatically built and releases an installable file whenever a new tag is introduced

#### Backend

Because frontend always needs the latest version of APIs, therefore, backend should be deployed whenever there are new changes merged into main. The whole continuous deployment workflow is powered by Github Actions, Docker, Kubernetes and AWS EKS (Amazon Web Services Elastic Kubernetes Service)

Intermediate steps (building docker images, connecting to AWS EKS, run tests, checking linting errors...) are done by Github Actions


## License

[MIT](https://choosealicense.com/licenses/mit/)
