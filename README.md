# 🧑‍💻 Coders of Delhi

A social-network-style recommendation engine built **entirely from scratch** using only Python's standard library — no external dependencies. This project simulates a mini social platform where users have friends and liked pages, and implements features like **"People You May Know"** and **"Pages You Might Like"** using fundamental data structures and algorithms.

---

## 📌 Project Overview

| Detail | Info |
|---|---|
| **Project Name** | Coders of Delhi |
| **Goal** | Build recommendation features from scratch without any external libraries |
| **Language** | Python 3.11+ (standard library only — `json` module) |
| **Format** | Jupyter Notebooks (`.ipynb`) |
| **Focus** | Data cleaning, preprocessing & recommendation algorithms |

---

## � Project Workflow

![Project Workflow](Project%20Coders%20of%20Delhi/Project_workflow.png)

---

## �🚀 Features

- 🔄 **Data Loading & Exploration** — Load and display users, friendships, and liked pages from JSON data
- 🧹 **Data Cleaning Pipeline** — Handle dirty data (missing names, duplicate friends, inactive users, duplicate pages)
- 👥 **People You May Know** — Recommend new connections based on mutual friends (friend-of-a-friend algorithm)
- 📚 **Pages You Might Like** — Suggest pages based on shared interests with other users

---

## 🗂️ Project Structure

```
Project Coders of Delhi/
├── 01_Introduction.ipynb          # Data loading & exploration
├── 02_data_cleaning.ipynb         # Data cleaning pipeline
├── people you may know.ipynb      # Friend recommendation algorithm
├── pages_you_might_like.ipynb     # Page recommendation algorithm
├── codebook_data.json             # Original clean dataset (4 users, 4 pages)
├── data2.json                     # Dirty dataset with intentional issues
├── cleaned_codebook_data.json     # Output of the cleaning pipeline
├── massive_data.json              # Larger dataset (30 users, 27 pages)
├── Project_workflow.png           # Visual workflow diagram
└── README.md
```

---

## 📓 Notebook Walkthrough

### 1️⃣ `01_Introduction.ipynb` — Data Loading & Exploration

Loads the social network data from `codebook_data.json` and displays all users with their connections (friends and liked pages) along with available community pages.

**Key functions:**
- `load_data(filename)` — Reads a JSON file and returns a Python dictionary
- `display_users(data)` — Pretty-prints all users and their connections

**Sample Output:**
```
Amit (ID: 1) - Friends: [2, 3] - Liked pages: [101]
Priya (ID: 2) - Friends: [1, 4] - Liked pages: [102]
...
```

---

### 2️⃣ `02_data_cleaning.ipynb` — Data Cleaning Pipeline

Processes the intentionally dirty dataset (`data2.json`) and outputs a clean version (`cleaned_codebook_data.json`).

**Cleaning steps performed by `clean_data(data)`:**

| Step | What It Does | Example Issue |
|---|---|---|
| Remove empty names | Filters out users with blank `name` fields | User ID 3 has `name: ""` |
| Deduplicate friends | Converts friend lists to sets to remove duplicates | Sara has `friends: [2, 2]` |
| Remove inactive users | Drops users with no friends AND no liked pages | User ID 5 has empty lists |
| Deduplicate pages | Keeps only unique pages by ID | Page 104 appears twice |

---

### 3️⃣ `people you may know.ipynb` — Friend Recommendations

Implements a **mutual friends algorithm** to suggest new connections — the same concept used by social platforms like Facebook and LinkedIn.

**How it works:**
1. Build a mapping of each user's direct friends
2. For each friend-of-a-friend, check if they are NOT already a direct friend
3. Count how many mutual friends exist with each potential suggestion
4. Sort suggestions by mutual friend count (highest first)

**Example:**
```
People You May Know for User 2 (Priya): [3]
# Priya → Amit → Rahul (Rahul is suggested via mutual friend Amit)
```

---

### 4️⃣ `pages_you_might_like.ipynb` — Page Recommendations

Implements a **collaborative filtering** approach to recommend pages based on what similar users have liked.

**How it works:**
1. Build a mapping of each user's liked pages
2. For each other user, calculate the number of shared/common liked pages
3. Pages liked by users with high overlap (but not yet liked by the target user) get higher scores
4. Return all suggestions sorted by relevance score

**Example (User 1 — Amit):**
```
Page 103 (AI & ML Community) — Score: 2
Page 105 (Blockchain Innovators) — Score: 1
...
```

---

## 📊 Data Format

The project uses JSON files with this schema:

```json
{
    "users": [
        {
            "id": 1,
            "name": "Amit",
            "friends": [2, 3],
            "liked_pages": [101]
        }
    ],
    "pages": [
        {
            "id": 101,
            "name": "Python Developers"
        }
    ]
}
```

---

## ⚙️ Getting Started

### Prerequisites

- **Python 3.11+** (no external packages needed!)
- **Jupyter Notebook** or **JupyterLab**

### Run the Project

```bash
# Clone the repository
git clone https://github.com/HarshitKamriya/Coders-of-Delhi.git
cd Coders-of-Delhi/Project\ Coders\ of\ Delhi

# Launch Jupyter
jupyter notebook
```

Run the notebooks in order:
1. `01_Introduction.ipynb` — Explore the data
2. `02_data_cleaning.ipynb` — Clean the dirty dataset
3. `people you may know.ipynb` — Get friend suggestions
4. `pages_you_might_like.ipynb` — Get page recommendations

---

## 🧠 Key Concepts Demonstrated

- **JSON data handling** using Python's built-in `json` module
- **Data cleaning & preprocessing** without pandas or numpy
- **Graph-based algorithms** — traversing friend-of-friend relationships
- **Collaborative filtering** — recommending items based on shared preferences
- **Set operations** — intersection, difference for efficient comparisons
- **Sorting with custom keys** — using lambda functions for ranked results

---

## 🛣️ Roadmap

- [ ] Add a **"Books You May Like"** recommendation feature
- [ ] Implement **interest-based matching** between users
- [ ] Build a **CLI or web interface** to interactively explore recommendations
- [ ] Scale to larger datasets with optimized algorithms

---

## 🤝 Contributing

Contributions are welcome! Feel free to fork the repo and submit a pull request.

---

## 📄 License

This project is open source and available for learning purposes.
