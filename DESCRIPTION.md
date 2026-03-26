# Project Description

## Overview

This repository is a **GitHub Skills exercise** designed to help you get started with [GitHub Copilot](https://github.com/features/copilot) — an AI-powered code completion and suggestion tool built into your editor. By working through this exercise, you will learn how to use GitHub Copilot to write code faster, explore unfamiliar APIs, and understand an existing codebase with the help of AI.

---

## The Sample Application

The exercise is built around a realistic sample project: the **Mergington High School Extracurricular Activities Management System**.

This is a lightweight web application that allows students to:

- **View** available extracurricular activities (Chess Club, Programming Class, Gym Class, and more).
- **Sign up** for activities using their school email address.

The application exposes a simple REST API powered by [FastAPI](https://fastapi.tiangolo.com/) and serves a browser-based front-end built with plain HTML, CSS, and JavaScript.

---

## Tech Stack

| Layer       | Technology                                      |
|-------------|--------------------------------------------------|
| Back-end    | [Python 3](https://www.python.org/) + [FastAPI](https://fastapi.tiangolo.com/) |
| Server      | [Uvicorn](https://www.uvicorn.org/) (ASGI server) |
| Front-end   | HTML5, CSS3, Vanilla JavaScript                  |
| Testing     | [pytest](https://pytest.org/) + [httpx](https://www.python-httpx.org/) |

---

## Project Structure

```
.
├── src/
│   ├── app.py          # FastAPI application — routes and in-memory data store
│   └── static/
│       ├── index.html  # Main web page
│       ├── styles.css  # Page styling
│       └── app.js      # Front-end JavaScript (fetches activities, handles sign-up)
├── requirements.txt    # Python dependencies
├── pytest.ini          # pytest configuration
└── DESCRIPTION.md      # This file
```

---

## API Endpoints

| Method | Path                                  | Description                              |
|--------|---------------------------------------|------------------------------------------|
| `GET`  | `/`                                   | Redirects to the front-end (`index.html`)|
| `GET`  | `/activities`                         | Returns the list of all activities       |
| `POST` | `/activities/{activity_name}/signup`  | Signs a student up for an activity       |

### Example — List activities

```http
GET /activities
```

```json
{
  "Chess Club": {
    "description": "Learn strategies and compete in chess tournaments",
    "schedule": "Fridays, 3:30 PM - 5:00 PM",
    "max_participants": 12,
    "participants": ["michael@mergington.edu", "daniel@mergington.edu"]
  },
  ...
}
```

### Example — Sign up for an activity

```http
POST /activities/Chess%20Club/signup?email=student@mergington.edu
```

```json
{
  "message": "Signed up student@mergington.edu for Chess Club"
}
```

---

## Getting Started

### Prerequisites

- Python 3.10 or later
- A GitHub account with access to GitHub Copilot

### Installation

1. **Clone the repository** (or open it in a Codespace — a `.devcontainer` configuration is included):

   ```bash
   git clone https://github.com/LogosoftEmirHardal/skills-getting-started-with-github-copilot.git
   cd skills-getting-started-with-github-copilot
   ```

2. **Install dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**:

   ```bash
   uvicorn src.app:app --reload
   ```

4. Open your browser and navigate to `http://127.0.0.1:8000` to see the front-end.

   The interactive API documentation (Swagger UI) is available at `http://127.0.0.1:8000/docs`.

### Running Tests

```bash
pytest
```

---

## Exercise Goals

By completing this exercise you will practise:

1. **Using GitHub Copilot suggestions** to write new features with minimal manual typing.
2. **Exploring an unfamiliar codebase** with Copilot's inline chat and explanations.
3. **Writing tests** guided by Copilot to improve code quality.
4. **Iterating quickly** by accepting, modifying, and rejecting Copilot suggestions.

---

## License

This project is licensed under the [MIT License](LICENSE).  
&copy; 2025 GitHub
