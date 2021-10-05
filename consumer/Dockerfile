# minimalistic erlang image
FROM erlang:alpine
# create workdir
RUN mkdir /app
# set workdir
WORKDIR /app
# define environment variables
ENV hostname consumer@consumer.com 
# copy the content of src into the workdir
COPY src/ /app
# compile the erlang file
RUN erlc consumer.erl
# define the entrypoint as the execution of the erlang file
ENTRYPOINT erl -name ${hostname} -setcookie cookie -noshell -run consumer start