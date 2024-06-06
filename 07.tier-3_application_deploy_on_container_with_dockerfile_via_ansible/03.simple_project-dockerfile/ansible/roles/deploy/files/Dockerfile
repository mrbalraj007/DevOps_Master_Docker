FROM ubuntu:latest

# Install dependencies
RUN apt-get update && apt-get install -y python3 python3-pip

# Copy application files
COPY ../../../../../app /app

# Install Python dependencies
RUN pip3 install -r /app/requirements.txt

# Set working directory
WORKDIR /app

# Expose port
EXPOSE 80

# Command to run the application
CMD ["python3", "app.py"]

