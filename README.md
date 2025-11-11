
# 📰 NewsscanAI

NewsscanAI is a web application built to classify news-related images using a deep learning model. Users can upload an image, and the application's pre-trained PyTorch model will analyze it and return a classification.

The application is built with a FastAPI backend, a simple Jinja2 template frontend, and is fully containerized with Docker for easy deployment.

## ✨ Features

  * **Image Classification:** Utilizes a pre-trained PyTorch Convolutional Neural Network (CNN) (`best_30_epochs.pt`) to classify uploaded images.
  * **Web Interface:** A simple, clean web UI for uploading images and viewing results, built with FastAPI and Jinja2 templates.
  * **Image Preprocessing:** Automatically processes uploaded images (resize, convert to tensor, normalize) to match the model's input requirements.
  * **Upload History:** A page to view a list of all previously uploaded images.
  * **Dockerized:** Includes a `Dockerfile` for easy, reproducible builds and deployment.

## 🛠️ Tech Stack

  * **Backend:** FastAPI, Uvicorn
  * **Frontend:** Jinja2, HTML, CSS
  * **Machine Learning:** PyTorch, Torchvision
  * **Image Processing:** Pillow (PIL), OpenCV, NumPy
  * **Containerization:** Docker

## 🚀 Getting Started

You can run this project either locally on your machine or as a Docker container.

### Prerequisites

  * Python 3.10+
  * Git
  * Docker (for containerized deployment)

### 1\. Running Locally

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/adithya95978/newsscanai.git
    cd Newsscanai
    ```

2.  **Create and activate a virtual environment (recommended):**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4.  **Create the `uploads` directory:**
    The `uploads` directory is ignored by Git, so you need to create it manually.

    ```bash
    mkdir uploads
    ```

5.  **Run the application:**

    ```bash
    uvicorn main:app --host 0.0.0.0 --port 8000
    ```

6.  **Open your browser:**
    Navigate to `http://localhost:8000` to use the application.

### 2\. Running with Docker

1.  **Build the Docker image:**
    From the root of the project directory, run:

    ```bash
    docker build -t newsscanai .
    ```

2.  **Run the Docker container:**
    This command maps port 8000 on your local machine to port 8000 inside the container.

    ```bash
    docker run -p 8000:8000 newsscanai
    ```

3.  **Open your browser:**
    Navigate to `http://localhost:8000` to use the application.

## 📁 File Structure

```
Newsscanai/
├── .gitignore
├── best_30_epochs.pt         # Pre-trained PyTorch model
├── Dockerfile                # Docker build instructions
├── main.py                   # FastAPI application logic and API endpoints
├── requirements.txt          # Python dependencies
│
├── helpers/
│   └── image_processing.py   # Image preprocessing function
│
├── static/
│   └── style.css             # CSS for the frontend
│
└── templates/
    ├── error.html            # Error page
    ├── index.html            # Main upload page
    ├── list_uploads.html     # Page to list uploaded images
    └── status.html           # Page to display prediction results
```
