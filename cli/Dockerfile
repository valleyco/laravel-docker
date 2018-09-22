ARG APP_NAME
FROM ${APP_NAME}_php-cli

RUN apt-get install -y git vim zip bash mc curl apt-transport-https ca-certificates gnupg2 libpng16-16 && \
  curl -sL https://deb.nodesource.com/setup_8.x | bash - && apt-get install -y nodejs build-essential && npm install npm -g

RUN useradd  --create-home  --shell /bin/bash valley; mkdir /home/valley/bin;chown valley:valley /home/valley/bin;
COPY comp_inst /home/valley/
COPY npm_setup /home/valley
RUN chown valley:valley /home/valley/*;chmod 755 /home/valley/comp_inst /home/valley/npm_setup

USER valley
ENV HOME /home/valley
RUN /home/valley/comp_inst;/home/valley/npm_setup;rm /home/valley/comp_inst /home/valley/npm_setup
RUN sed -ie 's/#alias/alias/g' ~/.bashrc; printf "\nPATH=/home/valley/bin:$PATH" >> /home/valley/.bashrc;

CMD  /bin/bash
