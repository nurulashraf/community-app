# Community Action Hub

A community issue reporting web app built with **Streamlit**, **MySQL**, and the **Google Gemini AI** API. Residents can log local problems and receive an AI-generated action plan to help resolve them.

---

## Features

- 📝 **Submit community issues** with a title, category, and detailed description
- 🤖 **AI-generated action plans** powered by Google Gemini 2.5 Flash
- 🗄️ **Persistent storage** using a local MySQL database
- 📋 **Neighbourhood Action Board** to view all previously logged issues

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | Streamlit |
| AI | Google Gemini 2.5 Flash (`google-genai`) |
| Database | MySQL (`mysql-connector-python`) |

---

## Prerequisites

- Python 3.8+
- MySQL Server running locally
- A [Google AI Studio API key](https://aistudio.google.com/api-keys)

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/nurulashraf/community-app.git
cd community-app
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure MySQL

Make sure MySQL is running on `localhost`. The app connects as `root` with no password by default.

If your MySQL setup uses a different username or password, update the connection settings in `app.py`:

```python
mydb = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password_here"
)
```

The app will automatically create the `community_issues` database and `issues` table on first run.

### 4. Run the app

```bash
streamlit run app.py
```

The app will open at **http://localhost:8501** in your browser.

### 5. Add your API key

In the sidebar, paste your **Google AI Studio API key** to enable AI-generated action plans.

---

## Project Structure

```
community-app/
├── app.py              # Main Streamlit application
├── test_db.py          # Script to test MySQL connection
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
    description TEXT NOT NULL,
    action_plan TEXT,
    timestamp   TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## License

This project is open source and available under the [MIT License](LICENSE).
