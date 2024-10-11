# Flask-Init

A Bash script to initialize a Flask project with customizable options, including virtual environment management, host and port settings, environment configuration, and additional page creation. It is designed for macOS.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Basic Usage](#basic-usage)
  - [Options](#options)
  - [Examples](#examples)
- [Project Structure](#project-structure)
- [How to Run the Generated Flask App](#how-to-run-the-generated-flask-app)
- [Managing the Virtual Environment](#managing-the-virtual-environment)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The `flask-init` script automates the setup of a Flask web application project. It handles the creation of a virtual environment, project directories, and files. Additionally, it allows you to specify custom host and port settings, choose between development and production environments, and create additional pages with ease.

## Features

- **Virtual Environment Management**: Automatically creates and manages a Python virtual environment.
- **Customizable Host and Port**: Set custom host and port for your Flask application.
- **Environment Configuration**: Choose between development and production environments.
- **Page Generation**: Create additional pages with corresponding templates and static files.
- **Logging Configuration**: Sets up logging using Loguru with secure permissions.
- **Project Structure Generation**: Generates a `README.md` with the project structure and usage instructions.

## Prerequisites

- **Bash Shell**: The script is written for Bash and requires a Unix-like environment.
- **Python 3.x**: Ensure Python 3 is installed on your system.
- **Git**: For version control (optional).

## Installation

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/nicojwn/flask-init.git
   ```

2. **Navigate to the Repository Directory**:

   ```bash
   cd <repository_directory>
   ```

3. **Make the flask-init Script Executable**:

4. **Add the Script to Your PATH** (optional):

   You can add the script to a directory that's in your `PATH` or modify your `PATH` to include the script's directory for easier access.

## Usage

The `flask-init` script must be **sourced** to properly handle virtual environment activation and deactivation.

```bash
source flask-init [arguments]
```

### Basic Usage

Initialize a new Flask project:

```bash
source flask-init my_flask_app
```

### Options

- `-dvenv`: Deactivate the current virtual environment.
- `-avenv`: Activate the virtual environment.
- `-pt <port>, --port <port>`: Set the port (default: `8080`).
- `-ht <host>, --host <host>`: Set the host (default: `0.0.0.0`).
- `-prod`: Set the environment to `'production'` (default: `'development'`).
- `-p [pages]`: Create additional pages (separated by space).
- `-h, --help`: Display the help message.

### Examples

1. **Initialize a New Flask Project**:

   ```bash
   source flask-init my_flask_app
   ```

2. **Create a Project with Additional Pages**:

   ```bash
   source flask-init my_flask_app -p about contact services
   ```

3. **Set Custom Host and Port**:

   ```bash
   source flask-init my_flask_app -ht 127.0.0.1 -pt 5000
   ```

4. **Set Production Environment**:

   ```bash
   source flask-init my_flask_app -prod
   ```

5. **Activate the Virtual Environment**:

   ```bash
   source flask-init -avenv
   ```

6. **Deactivate the Virtual Environment**:

   ```bash
   source flask-init -dvenv
   ```

7. **Combine Multiple Options**:

   Initialize a project with additional pages, set to production environment, and customize host and port:

   ```bash
   source flask-init my_flask_app -prod -pt 8000 -ht 127.0.0.1 -p about contact
   ```

## Project Structure

After running the script, your project directory will have the following structure:

```
<project_directory>/
├── README.md
├── requirements.txt
├── .venv/
├── logs/
│   └── app.log
├── app/
    ├── app.py
    ├── templates/
    │   ├── base.html
    │   ├── index.html
    │   ├── about.html    # If -p about was specified
    │   ├── contact.html  # If -p contact was specified
    ├── static/
        ├── css/
        │   └── style.css
        ├── js/
            ├── index.js
            ├── about.js    # If -p about was specified
            ├── contact.js  # If -p contact was specified
```

- **app/**: Contains the Flask application.
  - **app.py**: The main Flask application file.
  - **templates/**: HTML templates for rendering pages.
  - **static/**: Static files like CSS and JavaScript.
- **requirements.txt**: Lists the Python packages required for the project.
- **.venv/**: The Python virtual environment directory (hidden).
- **logs/**: Contains application logs.

## How to Run the Generated Flask App

1. **Activate the Virtual Environment**:

   ```bash
   source .venv/bin/activate
   ```

2. **Navigate to the App Directory**:

   ```bash
   cd app
   ```

3. **Run the Flask Application**:

   ```bash
   python app.py
   ```

4. **Access the Application**:

   Open your browser and go to `http://<host>:<port>/`.

   - **Default Host**: `0.0.0.0`
   - **Default Port**: `8080`

   If you specified custom host or port using `-ht` or `-pt`, use those values instead.

## Managing the Virtual Environment

### Activate the Virtual Environment

If the virtual environment is not already active, you can activate it using:

```bash
source flask-init -avenv
```

### Deactivate the Virtual Environment

To deactivate the current virtual environment, use:

```bash
source flask-init -dvenv
```

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the Repository**.
2. **Create a New Branch**:

   ```bash
   git checkout -b feature/YourFeature
   ```

3. **Commit Your Changes**:

   ```bash
   git commit -m "Add Your Feature"
   ```

4. **Push to the Branch**:

   ```bash
   git push origin feature/YourFeature
   ```

5. **Open a Pull Request**.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.