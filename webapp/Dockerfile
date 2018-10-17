FROM python:3.7-alpine as base

FROM base as builder

RUN mkdir /install
WORKDIR /install

RUN apk add python python-dev py2-pip autoconf automake g++ make libffi-dev --no-cache
COPY requirements.txt /requirements.txt

RUN pip install --install-option="--prefix=/install" -r /requirements.txt

FROM base

COPY --from=builder /install /usr/local
COPY . /app

WORKDIR /app

CMD ["python", "app.py"]
