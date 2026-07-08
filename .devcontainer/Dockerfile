FROM mambaorg/micromamba:1.5-jammy

USER root
RUN apt-get update && apt-get install -y git curl && rm -rf /var/lib/apt/lists/*

COPY environment.yml /tmp/environment.yml
RUN micromamba install -y -n base -f /tmp/environment.yml && \
    micromamba clean --all --yes

USER $MAMBA_USER
