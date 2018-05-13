# Use the barebones version of Ruby 2.2.3.
FROM ruby:2.3.3

# Install dependencies:
# - build-essential: To ensure certain gems can be compiled
# - nodejs: Compile assets
# - libpq-dev: Communicate with postgres through the postgres gem
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

# Set an environment variable to store where the app is installed to inside
# of the Docker image.
ENV INSTALL_PATH /todo
RUN mkdir -p $INSTALL_PATH

# This sets the context of where commands will be ran in and is documented
# on Docker's website extensively.
WORKDIR $INSTALL_PATH

# Ensure gems are cached and only get updated when they change. This will
# drastically increase build times when your gems do not change.
COPY Gemfile Gemfile
# Install all gems
RUN bundle install

# Copy in the application code from your work station at the current directory
# over to the working directory.
COPY . .
