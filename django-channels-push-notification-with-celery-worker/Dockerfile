FROM python:3.11.4-alpine

WORKDIR /usr/src/app

# prevent Python from writing .pyc files
ENV PYTHONDONTWRITEBYTECODE 1
# ensure Python output is sent directly to the terminal without buffering
ENV PYTHONUNBUFFERED 1

COPY pyproject.toml poetry.lock /usr/src/app/

RUN pip install poetry

RUN poetry config virtualenvs.create false && \
    poetry install --no-interaction --no-ansi

COPY core/entrypoint.sh /usr/src/app/entrypoint.sh

COPY core/ /usr/src/app/

ENTRYPOINT ["/usr/src/app/entrypoint.sh"]