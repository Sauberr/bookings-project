# Hotel Booking
This hotel booking application demonstrates the power of FastAPI and SQLAlchemy for building RESTful APIs. It incorporates Celery for asynchronous tasks, Redis for caching, Prometheus and Grafana for data monitoring and visualization  and Docker for containerization, showcasing a modern approach to backend development.

#### Stack:

- [Python](https://www.python.org/downloads/)
- [PostgreSQL](https://www.postgresql.org/)
- [Redis](https://redis.io/)
- [Celery](https://docs.celeryq.dev/en/stable/)
- [Docker](https://www.docker.com/)
- [Prometheus](https://github.com/trallnag/prometheus-fastapi-instrumentator)
- [Grafana](https://grafana.com/)

## Local Developing

All actions should be executed from the source directory of the project and only after installing all requirements.

1. Firstly, create and activate a new virtual environment:
   ```bash
   python3.11 -m venv ../venv
   source ../venv/bin/activate
   ```
   
2. Install packages:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

## Run application
The uvicorn web server is used to run FastAPI. The command to run looks like this:
```
uvicorn app.main:app --reload
```
It must be run on the command line, always being in the root directory of the project.

### Celery & Flower
To start Celery use the command
```
celery --app=app.tasks.celery:celery worker -l INFO -P solo

Note that `-P solo` is only used on Windows, as Celery has problems working on Windows.
To start Flower use the command
```
celery --app=app.tasks.celery:celery flower


### Dockerfile
To run a web server (FastAPI) inside a container, you need to uncomment the code inside the Dockerfile and have an already running PostgreSQL instance on your machine.
Code to run Dockerfile:
```
docker build .
```

The command is also run from the root directory where the Dockerfile resides.

### Docker compose
To start all services (DB, Redis, web server (FastAPI), Celery, Flower, Grafana, Prometheus), you need to use the docker-compose.yml file and the commands
```
docker compose build
docker compose up
```
Moreover, the `build` command needs to be run only if you changed something inside the Dockerfile, that is, you changed the logic for compiling the image.

## License

This project uses the [MIT] license(https://github.com/Sauberr/bookings-project/blob/master/LICENSE)

## Contact

To contact the author of the project, write to email 𝚍𝚖𝚒𝚝𝚛𝚒𝚢𝚋𝚒𝚛𝚒𝚕𝚔𝚘@𝚐𝚖𝚊𝚒𝚕.𝚌𝚘𝚖.
