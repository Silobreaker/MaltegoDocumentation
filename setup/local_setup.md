## Setting Up The Maltego Documentation Locally

Follow this [Github Pages guide](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/testing-your-github-pages-site-locally-with-jekyll) for the precise instructions on how to test the Maltego Documentation locally.

Once you have installed Jekyll, Ruby and Bundler, you should clone this repo to your machine and run `bundle exec jekyll serve --trace` to build the site and start the server. You should be able to access the site at `localhost:4000`.

> __Important__: If you are making changes to the [Gemfile](../Gemfile) you must remember to run ```bundle install``` to update the dependencies before building the site again.
