# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Install spaCy model
RUN python -m spacy download en_core_web_sm

# Define environment variable
ENV CELERY_BROKER_URL redis://redis:6379/0

# Run the Celery worker
CMD ["celery", "-A", "Automatic-News-Scrapper", "worker", "--loglevel=info"]
