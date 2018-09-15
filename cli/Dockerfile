ARG APP_NAME
FROM ${APP_NAME}_php-cli

RUN apt-get install -y git vim zip bash mc curl apt-transport-https ca-certificates gnupg2 libpng16-16 && \
  curl --fail -ssL -o setup-nodejs https://deb.nodesource.com/setup_8.x && \
  bash setup-nodejs && \
  apt-get install -y nodejs build-essential

RUN useradd  --create-home  --shell /bin/bash valley; mkdir /home/valley/bin;chown valley:valley /home/valley/bin;
COPY comp_inst /home/valley
RUN chown valley:valley /home/valley/comp_inst;chmod 755 /home/valley/comp_inst

USER valley
ENV HOME /home/valley
RUN /home/valley/comp_inst;rm /home/valley/comp_inst
RUN sed -ie 's/#alias/alias/g' ~/.bashrc; printf "\nPATH=/home/valley/bin:$PATH" >> /home/valley/.bashrc;
CMD  /bin/bash
