# Write-Jupyter-Notebook-Hello-World-using-Dev-Container-and-Dockerfile-with-python-3.12-slim in VS CODE
This will create a working environment for Jupyter Notebooks using Python 3.12-slim within a dev container. Code was generated through ChapGPT

Objective: Write Jupyter Notebook Hello World! using Dev Container and Dockerfile with python 3.12-slim.
Use vs Code for folder & file creation.

ChatGPT's Response: Here’s a step-by-step guide to create a Jupyter Notebook Hello World! project using a Dev Container with Dockerfile and Python 3.12-slim in VS Code:

### 1. Set Up VS Code
1. Install *VS Code* from [here](https://code.visualstudio.com/).
2. Install the *Dev Containers* extension from the Extensions Marketplace.
3. Install *Docker Desktop* from [here](https://www.docker.com/products/docker-desktop/) and ensure it’s running.

### 2. Create a Project Folder
1. Open VS Code.
2. Open a terminal within VS Code using *Ctrl + `*.
3. Run the following command to create a project directory:
   bash
   mkdir jupyter-dev-container
   cd jupyter-dev-container
   

### 3. Create Dev Container Setup
Inside the jupyter-dev-container folder, create a new directory called .devcontainer and add the required files:

1. **Create .devcontainer/devcontainer.json**:
   In the terminal or using VS Code’s file explorer, create a folder .devcontainer and inside it, a file named devcontainer.json.

   Add the following configuration in devcontainer.json:
   json
   {
     "name": "Python 3.12 Jupyter",
     "build": {
       "dockerfile": "Dockerfile"
     },
     "settings": {
       "terminal.integrated.shell.linux": "/bin/bash"
     },
     "extensions": [
       "ms-python.python",
       "ms-toolsai.jupyter"
     ],
     "postCreateCommand": "pip install jupyter"
   }
   

2. **Create .devcontainer/Dockerfile**:
   Next, create a Dockerfile inside the .devcontainer folder.

   Add the following to the Dockerfile:
   Dockerfile
   # Use the official Python 3.12 slim image
   FROM python:3.12-slim

   # Install essential packages
   RUN apt-get update && apt-get install -y \
       build-essential \
       && rm -rf /var/lib/apt/lists/*

   # Set the working directory
   WORKDIR /workspace

   # Install Jupyter
   RUN pip install --no-cache-dir jupyter

   # Expose Jupyter port
   EXPOSE 8888

   # Default command
   CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--no-browser", "--allow-root"]
   

### 4. Open the Dev Container
1. Now, inside VS Code, open the Command Palette using *Ctrl+Shift+P*.
2. Search for Dev Containers: Reopen in Container, and select it.

VS Code will build the container based on your Dockerfile and open the project within the dev container.

### 5. Create a Jupyter Notebook
1. Once the dev container is up, create a new file called hello_world.ipynb in the root folder.
2. Add the following Python code in the first cell:
   python
   print("Hello World!")
   

3. Run the cell to see the output.

### 6. Access Jupyter Notebook
If you want to access Jupyter Notebook in your browser:
1. Run the following command in the terminal (inside the container):
   bash
   jupyter notebook --ip=0.0.0.0 --allow-root
   
2. Copy the provided URL and open it in your browser to interact with Jupyter Notebook.

This will create a working environment for Jupyter Notebooks using Python 3.12-slim within a dev container.
