# DevOps course at Innopolis University

![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![CI](https://github.com/k05m0navt/devops/actions/workflows/ci.yaml/badge.svg?style=for-the-badge)

## Overview

Python Web App using [FastAPI framework](https://fastapi.tiangolo.com) and [WorldTimeAPI](http://worldtimeapi.org) for Moscow time.

## Getting Started

### Local installation

Before running the application, please install its prerequisites:

- [Python 3.9+](https://www.python.org/downloads/)
- [pip](https://pip.pypa.io/en/stable/installation/)

To run from the master branch, follow the instructions below:

1. Clone web application repository locally.
   ```bash
   git clone https://github.com/k05m0navt/devops
   ```
2. Create virtual environment.
   ```bash
   cd app_python/
   pipenv shell
   ```
3. Install packages.
   ```bash
   pipenv install
   ```
4. Run the application. Web app will open at [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

   ```bash
   uvicorn moscow_time.main:app --reload
   ```

### Docker

Before running the application, please install its prerequisites:

- [Docker 20.10.21+](https://docs.docker.com/get-docker/)

To run from the master branch, follow the instructions below:

1. Clone web application repository locally.
   ```bash
   git clone https://github.com/k05m0navt/devops
   ```
2. [Optional] Build the image.
   ```bash
   cd app_python/
   docker build -t k05m0navt/devops .
   ```
3. Run the container. Web app will open at [http://localhost:8000/](http://localhost:8000/).
   ```
   docker run -p 8000:8000 k05m0navt/devops
   ```

### Unit Testing

1. Make sure that you are in the application directory:
   ```bash
   cd devops/app_python
   ```
2. Run the tests:
   ```bash
   pytest tests
   ```

## Contacts

If you have any questions or ideas, write me in [Telegram](https://telegram.org): [@k05m0navt](https://t.me/k05m0navt/)
