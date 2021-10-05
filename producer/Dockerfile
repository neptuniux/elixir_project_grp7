# build the project with 
## docker build -t wichtf/producer:latest .
# push the project with 
## docker push wichtf/producer:latest
# instructions
## minimalistic erlang image
FROM erlang:alpine
## create workdir
RUN mkdir /app
## set workdir
WORKDIR /app
## define environment variables
ENV hostname producer@producer.com 
ENV PUID 1000
ENV PGID 1000
## copy the content of src into the workdir
COPY src/ /app
## compile the erlang file
RUN erlc producer.erl
## set the proper permissions
RUN chown -R ${PUID} /app
RUN chgrp -R ${PGID} /app
## change user because running as root is not recommended
USER ${PUID}
## define the entrypoint as the execution of the erlang file
ENTRYPOINT erl -name ${hostname} -setcookie cookie -noshell -run producer start