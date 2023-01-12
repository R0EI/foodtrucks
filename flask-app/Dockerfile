FROM python:2.7 as builder
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - \
 && apt-get install -y nodejs 
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM python:2.7.18-slim-stretch
COPY --from=builder ./app .
RUN pip install -r requirements.txt
EXPOSE 5000
ENTRYPOINT [ "python2", "app.py"]
