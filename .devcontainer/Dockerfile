FROM mcr.microsoft.com/devcontainers/python:3.10

# Install LaTeX and related packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    texlive-latex-base \
    texlive-latex-extra \
    texlive-fonts-recommended \
    texlive-fonts-extra \
    texlive-lang-portuguese \
    texlive-science \
    texlive-bibtex-extra \
    latexmk \
    cm-super \
    dvipng \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install AWS CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && ./aws/install \
    && rm -rf aws awscliv2.zip

# Set up Python environment
RUN pip install --no-cache-dir --upgrade pip setuptools wheel

# Install Jupyter and common extensions
RUN pip install --no-cache-dir \
    jupyter \
    jupyterlab \
    notebook \
    ipywidgets \
    jupyterlab-vim

# Create workspace directory
RUN mkdir -p /workspace
WORKDIR /workspace
