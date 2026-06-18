# Community Action Hub

Community Action Hub is a web application that enables residents to report local issues and receive structured, AI-generated action plans. Built with Streamlit and powered by Google Gemini, the application stores all submissions persistently in a MySQL database and displays them on a shared neighbourhood action board.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Database Schema](#database-schema)
- [License](#license)

---

## Features

- Submit community issues with a title, category, and detailed description
- AI-generated action plans using Google Gemini 2.5 Flash
- Persistent issue storage via a local MySQL database
- Neighbourhood Action Board displaying all previously reported issues in reverse chronological order

---

## Tech Stack

| Layer    | Technology                        |
|----------|-----------------------------------|
| Frontend | Streamlit                         |
| AI       | Google Gemini 2.5 Flash           |
| Database | MySQL                             |
| Language | Python 3.8+                       |

---

## Prerequisites

- Python 3.8 or higher
- MySQL Server running on localhost
- A Google AI Studio API key — obtain one at https://aistudio.google.com/api-keys

---

## Getting Started

**1. Clone the repository**

```bash
git clone https://github.com/nurulashraf/community-app.git
cd community-app
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Configure the database connection**

The application connects to MySQL on `localhost` using the `root` account with no password by default. If your MySQL instance uses different credentials, update the connection settings in `app.py`:

```python
mydb = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password_here"
)
```

The application will automatically create the `community_issues` database and `issues` table on first run.

**4. Run the application**

```bash
streamlit run app.py
```

The application will be accessible at `http://localhost:8501`.

**5. Configure your API key**

Enter your Google AI Studio API key in the sidebar to enable AI-generated action plans.

---

## Project Structure

```
community-app/
├── app.py              # Main Streamlit application
├── test_db.py          # MySQL connection test script
├── requirements.txt    # Python dependencies
└── README.md           # Project documentation
```

---

## Database Schema

```sql
CREATE TABLE issues (
    id          INT AUTO_INCREMENT PRIMARY KEY,
    title       VARCHAR(255) NOT NULL,
    category    VARCHAR(100) NOT NULL,
    description TEXT        NOT NULL,
    action_plan TEXT,
    timestamp   TIMESTAMP   DEFAULT CURRENT_TIMESTAMP
);
```

---

## License

This project is open source and available under the [MIT License](LICENSE).
