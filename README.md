# Story2Audio – Story to Audio Microservice

## Overview
Story2Audio converts written stories into expressive audio using **local NLP and TTS models**. It includes a **gRPC API**, a **Gradio frontend**, and **Dockerized deployment**. Developed as part of the *AI4001/CS4063 – Fundamentals of NLP Course*.

## Features
- Text preprocessing, enhancement (`falcon-rw-1b`), and TTS (`Kokoro-82M`)
- Audio stitching into a single `.mp3`
- gRPC API for scalable access
- Gradio interface for demos
- Docker support
- Unit & performance testing

## Project Structure
Story2Audio/
├── api/ # gRPC server & clients
├── src/ # Core pipeline (preprocessing, enhancement, TTS, utils)
├── tests/ # Unit & performance tests
├── Dockerfile
├── frontend.py # Gradio frontend
├── requirements.txt
└── story2audio.proto # gRPC service definition

bash
Copy code

## Installation
```bash
git clone <repository_url>
cd Story2Audio

# Create and activate virtual environment
python -m venv venv
venv\Scripts\activate   # Windows
source venv/bin/activate  # Linux/macOS

# Install dependencies
pip install -r requirements.txt
Install FFmpeg:

Windows: choco install ffmpeg

Linux: sudo apt-get install ffmpeg

macOS: brew install ffmpeg

Usage
Run gRPC Server
bash
Copy code
python api/server.py
Server runs at localhost:50051.

Run Gradio Frontend
bash
Copy code
python frontend.py
Access it via the displayed link (e.g., http://127.0.0.1:7860).

Docker Deployment
bash
Copy code
docker build -t story2audio .
docker run -p 50051:50051 story2audio
Testing
Run unit tests:

bash
Copy code
pytest tests/test_api.py
Run performance tests:

bash
Copy code
locust -f tests/performance_test.py --headless -u 10 -r 2 --run-time 1m
Limitations
CPU inference may be slow; GPU recommended.

TTS model may have accent/emotion limitations.

Gradio frontend is demo-grade, not production-ready.

Future Improvements
GPU acceleration

Advanced timeout and retry mechanisms

Production-grade frontend (React/Next.js)

Enhanced scalability for high concurrency
