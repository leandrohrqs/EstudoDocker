FROM python:3.10

RUN apt-get update && apt-get install -y python3-pip

WORKDIR /app

RUN pip install Flask
RUN pip install requests

COPY . .

EXPOSE 5000

CMD [ "python", "./app.py" ]