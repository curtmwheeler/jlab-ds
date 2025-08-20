FROM mambaorg/micromamba:1.5.8

WORKDIR /workspace
USER root
RUN apt-get update && apt-get install -y --no-install-recommends \
    tini locales && \
    rm -rf /var/lib/apt/lists/*

# Copy env first to leverage Docker cache on rebuilds
COPY environment.yml /tmp/environment.yml

# Create the env named "jlab" from environment.yml
RUN micromamba create -y -n jlab -f /tmp/environment.yml && \
    micromamba clean -a -y

# Make jlab the default at runtime (no "conda activate" needed)
SHELL ["/bin/bash", "-lc"]
ENV MAMBA_DOCKERFILE_ACTIVATE=1
ARG MAMBA_USER=mambauser

# Expose Jupyter
EXPOSE 8888

# Default command: launch JupyterLab from the jlab env
CMD ["bash", "-lc", "micromamba run -n jlab jupyter lab --ip=0.0.0.0 --port=8888 --no-browser --ServerApp.token='' --ServerApp.password='' --allow-root"]
