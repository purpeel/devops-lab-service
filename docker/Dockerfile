ARG PYTHON_VERSION=3.12.3
FROM python:${PYTHON_VERSION}-slim AS base

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /lab4
RUN mkdir app

ARG UID=10001
RUN adduser \
    --disabled-password \
    --gecos "" \
    --home "/nonexistent" \ 
    --shell "/sbin/nologin" \
    --no-create-home \
    --uid "${UID}" \
    appuser 

COPY ./app/requirements.txt ./app/requirements.txt
RUN python -m pip install -r ./app/requirements.txt

USER appuser

COPY ./app/ ./app
EXPOSE 5000

CMD uvicorn app.main:app --host 0.0.0.0 --port 5000