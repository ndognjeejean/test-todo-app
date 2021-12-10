FROM ubuntu:latest as git_source

# launch update of ubuntu
RUN apt update -y

# Install git
RUN apt install -y git

RUN mkdir /git_folder
WORKDIR /git_folder

# Clone repository of test
RUN git clone https://kongnuy@bitbucket.org/abysterdev/test-todo-app.git

FROM gradle:7.3.1-jdk11 as production

# copy repository of test from ubuntu test, in the before step
COPY --from=git_source /git_folder/test-todo-app/ /deploy/test-todo-app/
WORKDIR /deploy/test-todo-app

# command which will execute every time the container start
CMD ["gradle","bootRun"]

# expose port
EXPOSE 8087
