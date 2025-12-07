# Dockerfile - para agentes Jenkins que necesiten zip
FROM ubuntu:22.04

# Evitar preguntas interactivas
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      zip \
      unzip \
      git \
      ca-certificates \
      curl && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Opcional: crea un usuario jenkins (si prefieres NO correr como root)
# RUN useradd -m -s /bin/bash jenkins
# USER jenkins

WORKDIR /workspace

# Comando por defecto (no romperá pipeline)
CMD ["bash"]
