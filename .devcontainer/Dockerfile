# .devcontainer/Dockerfile
FROM mambaorg/micromamba:1.5-jammy

USER root
RUN apt-get update && apt-get install -y git curl build-essential && rm -rf /var/lib/apt/lists/*

COPY environment.yml /tmp/environment.yml
RUN micromamba install -y -n base -f /tmp/environment.yml && \
    micromamba clean --all --yes

# ichorCNA is not on Bioconductor/CRAN — install from the vendored source in the repo
COPY ichorCNA /tmp/ichorCNA
RUN micromamba run -n base R CMD INSTALL /tmp/ichorCNA

RUN echo "source /usr/local/bin/_activate_current_env.sh" >> /etc/bash.bashrc

USER $MAMBA_USER
ENV PATH="/opt/conda/bin:$PATH"