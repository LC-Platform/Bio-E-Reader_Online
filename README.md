# Bio E-Reader (Online)

**Bio E-Reader** is a web-based reading application developed as part of the LC Platform ecosystem. It provides an interface for accessing structured textual content, multilingual translations, domain-specific vocabulary, and supplementary learning resources.

The application uses React for the frontend, FastAPI for backend API services, and MongoDB for data storage.

## Overview

The Bio E-Reader provides a digital environment for reading and exploring structured content. It connects a web-based interface to backend services that retrieve and process content from the configured database.

The project is organized into two primary components:

- **Frontend:** A React application that provides the user interface.
- **Backend:** A Python application built with FastAPI that exposes APIs for accessing content and related resources.

MongoDB serves as the data store for the application's content collections.

## Features

- **Digital Reading:** Access and explore structured textual content.
- **Chapter and Segment Organization:** Work with content organized into chapters and segments, where supported by the dataset.
- **Multilingual Content:** Access available text and translations.
- **Domain Vocabulary:** Explore domain-specific terminology and vocabulary entries.
- **Approved Words:** Access approved vocabulary data.
- **Translated Sentences:** Retrieve translated sentence content.
- **Supplementary Resources:** Access supporting materials such as labeled images, process videos, and questions, where available.
- **REST API:** Retrieve content through FastAPI endpoints.
- **MongoDB Integration:** Access content stored in MongoDB through the backend.

## Technology Stack

| Component         | Technology  |
| ----------------- | ----------- |
| Frontend          | React       |
| Backend           | Python      |
| API Framework     | FastAPI     |
| ASGI Server       | Uvicorn     |
| Database          | MongoDB     |
| API Communication | HTTP / REST |

## System Architecture

The application follows a client-server architecture.

```text
                 BIO E-READER
                      |
          +-----------+-----------+
          |                       |
          v                       |
   React Frontend                 |
          |                       |
          | HTTP Requests         |
          v                       |
   FastAPI Backend                |
          |                       |
          | Database Queries      |
          v                       |
       MongoDB                    |
          |                       |
          +-----------------------+
```

### Frontend

The React frontend provides the user-facing reading interface and communicates with the backend to retrieve application data.

### Backend

The FastAPI backend handles API requests, data retrieval, and communication with MongoDB.

### Database

MongoDB stores the content and supporting resources used by the application.

## Repository Structure

The repository contains the following main directories:

```text
Bio-E-Reader_Online/
│
├── concept-accessor-user-side-main/
│   ├── userapi.py
│   └── requirements.txt
│
├── textbook-tool/
│   └── React frontend application
│
├── .vscode/
├── USR.txt
├── input.txt
├── input.txt.conllu
├── docker-commands.txt
├── insert_summary_audio.py
├── insert_usr_for_sentences.py
└── README.md
```

**Note:** This is a simplified representation based on the visible repository contents. The complete directory structure and additional files may vary.

### Key Components

| File or Directory                    | Description                                                   |
| ------------------------------------ | ------------------------------------------------------------- |
| `concept-accessor-user-side-main/` | Contains the backend application components.                  |
| `userapi.py`                       | FastAPI backend entry point.                                  |
| `requirements.txt`                 | Python dependencies for the backend.                          |
| `textbook-tool/`                   | Contains the React frontend application.                      |
| `USR.txt`                          | USR-related data or input, depending on its current contents. |
| `input.txt`                        | Input data used by the relevant processing workflow.          |
| `input.txt.conllu`                 | CoNLL-U formatted linguistic data.                            |
| `docker-commands.txt`              | Reference commands for Docker-related workflows.              |
| `insert_summary_audio.py`          | Script related to inserting summary audio data.               |
| `insert_usr_for_sentences.py`      | Script related to inserting USR data for sentences.           |

Some repository files support data preparation or linguistic processing rather than the core online reader.

## Prerequisites

Before running the application, ensure that you have:

- Python 3.
- pip.
- Node.js and npm.
- Access to a MongoDB database.
- Git.

Additional dependencies may be required depending on the frontend and backend configuration.

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/LC-Platform/Bio-E-Reader_Online.git

cd Bio-E-Reader_Online
```

### 2. Set Up the Backend

Navigate to the backend directory:

```bash
cd concept-accessor-user-side-main
```

Create a Python virtual environment.

**Linux/macOS**

```bash
python3 -m venv venv
source venv/bin/activate
```

**Windows**

```powershell
python -m venv venv
venv\Scripts\activate
```

Install the backend dependencies:

```bash
pip install -r requirements.txt
```

### 3. Configure MongoDB

Configure the backend with the appropriate MongoDB connection settings.

Before starting the application, verify that:

- MongoDB is accessible.
- The connection configuration is correct.
- The required database and collections are available.
- The application has the necessary permissions.

Keep database credentials and other sensitive configuration out of the repository.

### 4. Run the Backend

From the directory containing `userapi.py`, start the FastAPI server:

```bash
uvicorn userapi:app --host 127.0.0.1 --port 8000
```

This command assumes the FastAPI application instance is named `app`.

The backend will be available at:

`http://127.0.0.1:8000`

If FastAPI's interactive documentation is enabled, you can explore the API at:

`http://127.0.0.1:8000/docs`

### 5. Run the React Frontend

Open a new terminal and navigate to the frontend directory:

```bash
cd textbook-tool
```

Install the frontend dependencies:

```bash
npm install
```

Start the frontend using the script defined in `package.json`. For a Vite-based project, the command is typically:

```bash
npm start
```

Configure the frontend to communicate with the FastAPI backend using the appropriate API base URL.

The exact frontend commands depend on the scripts defined in the project's `package.json`.

## API Integration

The React frontend communicates with the FastAPI backend through HTTP requests.

The general request flow is:

1. The user interacts with the React interface.
2. The frontend sends a request to the backend.
3. FastAPI processes the request.
4. The backend retrieves the required information from MongoDB.
5. The backend returns a response to the frontend.
6. The frontend displays the retrieved content.

The available endpoints and response formats depend on the current backend implementation.

## Configuration

The application may require configuration for:

- MongoDB connection settings.
- Backend API URL.
- Frontend API base URL.
- Additional environment variables used by the application.

Use the configuration mechanism already implemented in the project.

Do not commit passwords, API keys, access tokens, or production database credentials to GitHub.

## Troubleshooting

### Backend Does Not Start

- Verify that the Python virtual environment is activated.
- Check that all dependencies are installed.
- Confirm that the FastAPI application entry point is correct.
- Ensure the configured port is available.
- Review the terminal output for errors.

### MongoDB Connection Issues

- Verify the MongoDB connection settings.
- Confirm that the database is reachable.
- Check authentication and database permissions.
- Ensure that the expected collections exist.

### Frontend Cannot Connect to the Backend

- Confirm that the FastAPI server is running.
- Verify the backend URL configured in React.
- Check browser developer tools for network errors.
- Configure CORS if the frontend and backend run on different origins.

## Contributing

Contributions that improve the reading interface, backend APIs, data access, and application documentation are welcome.

To contribute:

1. Fork the repository.
2. Create a feature branch.
3. Implement your changes.
4. Test the relevant functionality.
5. Submit a pull request describing your changes.

Please avoid committing credentials, private datasets, or other sensitive information.

## License

Refer to the repository's `LICENSE` file for the applicable licensing terms.

If no license file exists, add an appropriate license before distributing the source code for reuse.

## Acknowledgements

Bio E-Reader is part of the LC Platform ecosystem and builds on open-source technologies, including React, FastAPI, and MongoDB.

## Repository

**GitHub:** https://github.com/LC-Platform/Bio-E-Reader_Online
