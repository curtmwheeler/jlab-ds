# 🐳 JLab DS – Docker Setup (`/docker`)

This directory contains all configuration files required to run the **JupyterLab Data Science environment** in Docker.
It provides a reproducible R + Python environment for Data Science & AI coursework.

---

## ⚠️ Warning

Do **not** modify these core files unless you fully understand the implications:

* [`Dockerfile`](Dockerfile) – defines the base image and environment build process
* [`docker-compose.yml`](docker-compose.yml) – service orchestration (ports, volumes, restart policy)
* [`.dockerignore`](.dockerignore) – specifies files excluded from the Docker context

Changes here may break the development environment. If you need customizations, create a `docker-compose.override.yml` at the project root.

---

## 📂 File Overview

* **`Dockerfile`** –
  Uses [micromamba](https://github.com/mamba-org/micromamba-docker) for fast conda environments.
  Installs Python, R, JupyterLab, and packages listed in `environment.yml`.
  Exposes port **8888** and launches JupyterLab on container start.

* **`docker-compose.yml`** –
  Defines a single service `jlab` which:

  * Builds from the Dockerfile
  * Mounts the project root at `/workspace` inside the container
  * Publishes JupyterLab on `localhost:8888`
  * Restarts automatically unless stopped

* **`.dockerignore`** –
  Prevents unnecessary files (caches, logs, data, Git history, etc.) from bloating the Docker image.

---

## ▶️ Quick Start

From the project root (not just `/docker`):

1. **Build the image**

   ```bash
   docker compose -f docker/docker-compose.yml build
   ```

2. **Start JupyterLab**

   ```bash
   docker compose -f docker/docker-compose.yml up
   ```

   Access at: [http://localhost:8888](http://localhost:8888)

3. **Stop the container**

   ```bash
   docker compose -f docker/docker-compose.yml down
   ```

---

## 🔒 Authentication

For convenience, this configuration **disables Jupyter token/password login**.
If you plan to expose this outside your machine, update the `CMD` in `Dockerfile` or add overrides in `docker-compose.override.yml` to enable authentication.

---

## 💡 Extending

* Add packages → edit `environment.yml` (root directory), then rebuild:

  ```bash
  docker compose -f docker/docker-compose.yml build --no-cache
  ```
  
* Override configs → create `docker-compose.override.yml` at the project root instead of editing files here.

---

## 🐞 Troubleshooting

* **“Conda environment not found”** → ensure `environment.yml` exists at project root before building.
* **Port 8888 already in use** → change the port mapping in `docker-compose.yml` (`"8889:8888"`).
* **Permission errors on volumes** → ensure Docker Desktop/engine has access to your project directory.
