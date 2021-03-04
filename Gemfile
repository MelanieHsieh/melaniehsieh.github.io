source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins

install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.0", :install_if => Gem.win_platform?

# kramdown v2 ships without the gfm parser by default. If you're using
# kramdown v1, comment out this line.
gem "kramdown-parser-gfm"

group :jekyll_plugins do
    gem 'jekyll-feed', '~> 0.13.0'
    gem 'jekyll-sitemap', '~> 1.4'
    gem 'jekyll-compose', '~> 0.12.0'
    gem 'jekyll-postfiles', '~> 3.1'
  end 