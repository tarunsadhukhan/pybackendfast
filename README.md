
# Dockerfile
FROM python:3.13-slim

# Set the working directory
WORKDIR /app

# Copy requirements and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the project files
COPY . .

# Expose the app port
EXPOSE 5004

# Start the FastAPI server
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "5004"]

# create requirement.txt

mysql-connector-python

fastapi==0.100.0
uvicorn==0.22.0
pydantic==2.1.1
python-dotenv
python-jose
passlib



# for Creation of Docker file 
docker build -t pybackendfast .

# run the docker file
docker run -p 5004:5004 pybackendfast
# if want to run another port targetport 8000 source port 5004 which is mentioned in dockerfile
docker run -p 8000:5004 pybackendfast

# push to dockur hub ( pls ensure that logged in Docker Hub)
docker tag pybackendfast <your-dockerhub-username>/pybackendfast:latest
docker push <your-dockerhub-username>/pybackendfast:latest

# pull from docker hub
docker pull <your-dockerhub-username>/pybackendfast:latest

