# LeetCode Solutions Archive

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](/LICENSE)

A **fully automated archive of LeetCode problems** with complete solutions, multiple approaches, and time/space complexities. This repository provides a **static website** for browsing, searching, and filtering problems using Vanilla JS, and it is designed to be **scalable and contributor-friendly**.

## 🌟 Project Overview

**Purpose:**  
- Store all LeetCode problems in a structured format.  
- Provide multiple solution approaches with detailed explanations.  
- Include time and space complexity for every approach.  
- Enable browsing and filtering through a static website.  
- Automate data generation and validation for contributors.  

**Key Features:**  
- Multi-language solutions: C++, Java, Python.  
- Problem metadata: difficulty, topics, companies, curated sets.  
- Automation: build `data/` folder from `problems/` using `buildData.js`.  
- Validation: ensure problem folders and metadata are correct using `validate.js`.  
- Vanilla JS frontend: no framework needed, easy deployment.  
- CI/CD ready: validation and deployment automated via GitHub Actions.  

## 📂 Repository Structure

```bash
leetcode-solutions-archive/
├── src/                             # Editable frontend source
│   ├── index.html                   # Homepage template
│   ├── problem.html                 # Problem detail page
│   ├── css/
│   │   └── styles.css
│   └── js/
│       ├── main.js                  # Problem list rendering
│       ├── problem.js               # Problem details rendering
│       └── utils.js                 # Markdown rendering, filters, helpers
│
├── public/                          # Static assets (images, favicon)
│   └── favicon.ico
│
├── problems/                        # Raw problem folders (content layer)
│   ├── 0001-two-sum/
│   │   ├── README.md                # Problem statement
│   │   ├── metadata.json            # Problem metadata
│   │   └── solutions/
│   │       ├── cpp/hashmap.cpp
│   │       ├── java/hashmap.java
│   │       └── python/hashmap.py
│   └── ...
│
├── data/                            # Auto-generated indexes (never manually edited)
│   ├── problems.json
│   ├── tags.json
│   ├── companies.json
│   └── sets/
│       ├── top-150.json
│       ├── blind-75.json
│       └── faang-100.json
│
├── scripts/                         # Automation tooling (Node.js)
│   ├── buildData.js                 # Generates data/ from problems/
│   └── validate.js                  # Ensures metadata, file paths, and structure are correct
│
├── dist/                             # Deployment-ready site
│   ├── index.html
│   ├── problem.html
│   ├── js/
│   ├── css/
│   └── data/
│
├── .github/
│   └── workflows/
│       └── ci.yml                   # CI → validate + build data + deploy
│
├── README.md
├── CONTRIBUTING.md
├── LICENSE.md
└── .gitignore
```

## 🛠 Problem Folder Structure

Each problem folder should include:
```bash
problems/{id}-{slug}/
├── README.md               # Problem statement in markdown
├── metadata.json           # Problem metadata and approaches
└── solutions/
    ├── cpp/solution.cpp
    ├── java/solution.java
    └── python/solution.py
```

### Example `metadata.json`:
```json
{
  "id": 1,
  "slug": "two-sum",
  "title": "Two Sum",
  "difficulty": "easy",
  "topics": ["Array", "HashMap"],
  "companies": ["Amazon", "Google"],
  "approaches": [
    {
      "name": "Brute Force",
      "description": "Try every pair of numbers to find the solution.",
      "complexity": { "time": "O(n^2)", "space": "O(1)" },
      "languages": { "cpp": "solutions/cpp/brute_force.cpp" }
    },
    {
      "name": "HashMap",
      "description": "Use a hash map to find complements in one pass.",
      "complexity": { "time": "O(n)", "space": "O(n)" },
      "languages": {
        "cpp": "solutions/cpp/hashmap.cpp",
        "java": "solutions/java/hashmap.java",
        "python": "solutions/python/hashmap.py"
      }
    }
  ]
}
```

## 🔹 Automation Scripts

### `validate.js`
This script ensures that every problem folder follows the required structure and rules:
- ✅ Checks each problem folder for required files (`README.md`, `metadata.json`, `solutions/`)  
- ✅ Validates the structure and fields of `metadata.json`  
- ✅ Ensures unique IDs and slugs across all problems  
- ✅ Confirms proper folder and file organization  

### `buildData.js`
This script generates the `data/` folder used by the frontend:
- 📄 Creates `problems.json` → master list of all problems  
- 🏷️ Creates `tags.json` → list of unique tags for filtering  
- 🏢 Creates `companies.json` → list of companies for filtering  
- 📚 Generates curated sets:
  - `top-150.json`  
  - `blind-75.json`  
  - `faang-100.json`  

## 🛠 Frontend Usage

- **Homepage (`index.html`)**  
  Browse all problems, filter by difficulty, topic, company, or curated set.  

- **Problem Page (`problem.html`)**  
  View problem statement, solution approaches, code snippets, and time/space complexity.  

- **Markdown Rendering**  
  Problem statements are parsed directly from `README.md`.  

- **Filters & Search**  
  Implemented with Vanilla JS using JSON files inside the `data/` folder.  

## 🚀 Workflow

1. **Add or update a problem** in the `problems/` folder.  
2. **Run validation locally**:  
   ```bash
   node scripts/validate.js
   ```
3. **Build `data/` for frontend**:
   ```bash
   node scripts/buildData.js
   ```   
4. **Commit and push** → CI/CD will validate and deploy automatically.

## 🤝 Contributing

- Fork the repository  
- Add problems following folder and metadata conventions  
- Validate and build data locally before committing  
- Open a pull request  
> Ensure consistency in metadata, folder structure, and code organization  

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](/LICENSE). 
