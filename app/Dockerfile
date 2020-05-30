FROM python:3.8.1-alpine

LABEL maintainer="GhostKU <dev@ghostku.com>" \
      description="Telegram Bot"

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV PATH "/usr/src/app/scripts:${PATH}"

EXPOSE 80
WORKDIR /usr/src/app


# встановлюємо залежності
RUN set -eux \
    && apk add --no-cache --virtual .build-deps build-base \
        gcc  python3-dev
        #  libressl-dev libffi-dev \ 
        # postgresql-dev musl-dev

# копіюємо файл з вимогами 
COPY ./requirements /usr/src/app/requirements

# Встановлюємо залежності в pip
RUN pip install --upgrade pip setuptools wheel \
    && pip install -r /usr/src/app/requirements/prod.txt \
    && rm -rf /root/.cache/pip

RUN pip install -r /usr/src/app/requirements/dev.txt \
    && rm -rf /root/.cache/pip

# копіюємо проєкт
COPY . /usr/src/app/

ENTRYPOINT ["python3", "bot.py"]