# ./Dockerfile

# Extend from the official Elixir image
FROM elixir:latest

# Install postgress-client
RUN apt-get update && \
  apt-get install -y postgresql-client

# Create app directory and copy the Elixir projects into it
RUN mkdir /app
COPY . /app
RUN chmod +x /app/entrypoint.sh
WORKDIR /app

# Install hex package manager
# By using --force, we don’t need to type “Y” to confirm the installation
RUN mix local.hex --force

# Get the dependency
RUN mix deps.get

# Compile the project
RUN mix do compile

# run script
CMD ["/app/entrypoint.sh"]