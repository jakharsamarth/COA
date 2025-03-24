# 🐳 Dockerized Streamlit Development Environment

Welcome to your **Dockerized Streamlit Development Environment**! This setup ensures a smooth, containerized experience for building and running your Streamlit applications.

---

## ✅ **Prerequisites**
Ensure the following are installed before proceeding:

- **Docker** 🐳 *(Ensure the Docker daemon is running)*
- **Python 3.9+** 🐍 *(Verify with `python --version`)*
- **pip** *(Confirm with `pip --version`)*
- Basic knowledge of **Streamlit** 📊 *(Not mandatory but helpful)*

---

## 📁 **Project Structure**

Here's how your project is organized:

```
project_root/
├── .streamlit/
│   └── config.toml          # Streamlit configuration
├── src/
│   └── main.py              # Streamlit app logic
├── Dockerfile               # Docker build instructions
├── requirements.txt         # Python dependencies
└── README.md                # Project guide (you're here!)
```

---

## 🧾 **File Overview**

### 📌 `.streamlit/config.toml`
Configures local Streamlit settings to improve the development experience.
```toml
[server]
headless = true
runOnSave = true
fileWatcherType = "poll"
```

### 📌 `src/main.py`
The main application file for Streamlit. Features include:
- **🏠 Home Page:** Introduction to the app.
- **📊 Data Explorer:** Upload and explore CSV files.
- **📈 Visualization Page:** Generate interactive charts and graphs using Plotly and Matplotlib.

### 📌 `Dockerfile`
Defines the container environment for your Streamlit app.
```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt
COPY . /app/
EXPOSE 8501
CMD ["streamlit", "run", "src/main.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

### 📌 `requirements.txt`
Lists all required dependencies:
```
streamlit
pandas
numpy
matplotlib
plotly
```

---

## 🚀 **How to Run the Project**

Follow these steps to build and run the app using Docker:

1. **Navigate to the Project Directory:**
```bash
cd path/to/project_root
```

2. **Build the Docker Image:**
```bash
docker build -t streamlit-app .
```

3. **Run the Docker Container:**
```bash
docker run -p 8501:8501 streamlit-app
```

4. **Access the App:**
- Open your browser and visit: [http://localhost:8501](http://localhost:8501)

---

## 🛠 **Development Tips**

- **Live Reloading:** With `runOnSave = true`, changes in your code will automatically reflect on the app when saved.
- **Error Debugging:** Check the container logs using:
```bash
docker ps            # Get container ID
docker logs <container_id>
```
- **Stopping the Container:**
```bash
docker stop <container_id>
```

---

## 🎯 **Conclusion**
You now have a fully functional Streamlit app running in a Docker container. Happy coding and data visualizing! 🚀

For further information on Streamlit, visit the official [Streamlit Documentation](https://docs.streamlit.io/).

