FROM selenium/standalone-chrome:3.141.59

USER root
RUN apt-get update && apt-get install -y --no-install-recommends python-pip && pip install selenium && rm -rf /var/lib/apt/lists/*
