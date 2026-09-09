source "https://rubygems.org"

# GitHub Pages builds this repository with the `github-pages` gem, which pins Jekyll
# and every whitelisted plugin to the versions used in production
# (see https://pages.github.com/versions/). Using the same gem locally keeps
# `bundle exec jekyll serve` identical to what GitHub Pages publishes.
gem "github-pages", group: :jekyll_plugins

# Local development server (webrick is no longer a default gem since Ruby 3.0).
gem "webrick", "~> 1.8"

# Windows and JRuby do not include zoneinfo files.
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]
