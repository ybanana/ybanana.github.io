# frozen_string_literal: true

source "https://rubygems.org"
gemspec

gem "jekyll", ENV["JEKYLL_VERSION"] if ENV["JEKYLL_VERSION"]
gem "kramdown-parser-gfm" if ENV["JEKYLL_VERSION"] == "~> 3.9"

gems:
  - jekyll-paginate-v2

group :jekyll_plugins do
    gem "jekyll-paginate-v2"
    gem "jekyll-feed"
  end