FROM selenium/standalone-firefox:3.141.59

USER root
RUN apt-get update && apt-get install -y python-pip && pip install selenium
RUN useradd -ms /bin/sh user
RUN chmod a+x /usr/bin/geckodriver

USER user
WORKDIR /home/user