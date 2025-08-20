# 📊 JLab DS - Data Science Environment

> ⚠️ **Heads up:** We’re working on a **simple installer CLI**. Soon, you’ll be able to type a single command, and everything will be set up for you automatically. No manual setup required. 🎉

---

## 🚀 Project Overview

This project provides a ready-to-use **data science environment** that includes:

* **Python** 🐍 (for machine learning, AI, and general coding)
* **R** 📈 (for data science, statistics, and visualization)
* **JupyterLab** 💻 (a web-based interactive environment for writing code and analyzing data)

<details>
  <summary>🤔 What does this mean in plain English?</summary>  
  This project gives you a pre-built “science lab” on your computer so you don’t have to install all the tools one by one.  
</details>

---

## 🛠️ Installation Instructions

### Step 1: Install Docker

* Install here: [Download Docker Desktop](https://www.docker.com/products/docker-desktop)

<details>
  <summary>🤔 What is Docker?</summary>  
  Docker is like a **magic box** that contains everything you need. It makes sure things work the same on every computer.  
  Think of Docker as a lunchbox. Instead of buying all the ingredients, the lunchbox already has your meal inside—ready to eat.  
</details>

---

### Step 2: Clone the Repository

Run this in your terminal:

```bash
git clone https://github.com/curtmwheeler/jlab-ds.git
cd jlab-ds/docker
```

<details>
  <summary>🤔 What does "clone" mean?</summary>  
  “Cloning” just means copying the project from the internet (GitHub) onto your computer.  
</details>

---

### Step 3: Start the Environment

Run:

```bash
docker compose up
```

This will:

* Download the tools (Python, R, JupyterLab)
* Build your environment
* Start JupyterLab at [http://localhost:8888](http://localhost:8888)

<details>
  <summary>🤔 What happens after I run this?</summary>  
  After running this, open your browser and go to the link. You’ll see **JupyterLab**, which is like Microsoft Word for code and data science.  
</details>

---

## 📂 Project Structure

```
┌── docker
│   ├── docker-compose.yml
│   ├── Dockerfile
│   └── README.md
├── environment.yml
├── LICENSE.md
├── README.md
└── src
    ├── projects
    │   ├── config_check
    │   └── README.md
    └── README.md
```

<details>
  <summary>🤔 Do I need to understand this?</summary>  
  Don’t worry if this looks technical. These are just “setup instructions” for the computer.  
</details>

---

## ✅ Features

* Works on **Mac, Windows, and Linux**
* Includes **Python + R kernels** for JupyterLab
* Comes pre-loaded with **popular data science libraries**
* Automatically rebuilds if you update `environment.yml`

---

## 🧑‍💻 For Developers

* Build manually:

  ```bash
  docker build -t jlab-ds .
  ```

* Rebuild after editing `environment.yml`:

  ```bash
  docker compose build --no-cache
  ```

---

## 🔮 Coming Soon

* **One-command installer CLI** (no Docker knowledge required)
* Pre-configured git setup
* Automatic environment updates
