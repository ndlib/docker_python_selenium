FROM selenium/standalone-chrome:3.141.59

USER root
RUN apt-get update && apt-get install -y --no-install-recommends python3-pip && pip3 install selenium && rm -rf /var/lib/apt/lists/*
