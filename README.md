# SIT323 - Task 5.1P: Dockerised Calculator Microservice

This is my submission for Task 5.1P in Cloud Native Application Development.  
I built a basic calculator API using Node.js and Express, then containerised it using Docker and Docker Compose.

## Tools Used
- Node.js and Express for the backend
- Docker and Docker Compose to containerise the app
- Visual Studio Code for development
- GitHub for version control

## How to Run the App (Dockerised)

### Step 1: Clone the Repository
git clone https://github.com/s223060317/sit323-2025-prac5p.git
cd sit323-2025-prac5p

### Step 2: Start the Container
Make sure Docker Desktop is running, then run:
docker-compose up --build
The terminal should show:  
'Server is running on port 3000'

## How to Test the API

Once running, open your browser or Postman and try the following endpoints:

- http://localhost:3000/add?num1=5&num2=3
- http://localhost:3000/subtract?num1=10&num2=4
- http://localhost:3000/multiply?num1=2&num2=6
- http://localhost:3000/divide?num1=20&num2=5

### Expected Output
{ "result": 8 }
If inputs are invalid or missing:
{ "error": "Both num1 and num2 must be valid numbers." }

## Dockerfile

FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]

## docker-compose.yml
services:
  calculator:
    build: .
    ports:
      - "3000:3000"

## GitHub Repository

https://github.com/s223060317/sit323-2025-prac5p
