
FROM python:3.9.6-slim

WORKDIR /app
COPY requirements.txt /app/

# Mise à jour du système de base et les packages
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y --no-install-recommends gcc g++ make && \
    pip install --no-cache-dir -r requirements.txt && \
    
    #Suppression des dépendances de construction pour réduire la taille de l'image
    apt-get remove --purge -y build-essential && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

COPY . /app
RUN useradd -m -d /home/kaide -s /bin/bash kaide && \
    chown -R kaide:kaide /app

USER kaide
EXPOSE 80
ENV NOM kaide
CMD ["python", "app.py"]

