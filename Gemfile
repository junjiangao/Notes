source "https://rubygems.org"

# Jekyll version
gem "jekyll", "~> 4.3.0"

# Jekyll theme - Chirpy
gem "jekyll-theme-chirpy", "~> 6.0"

# Plugins
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.17"
  gem "jekyll-sitemap", "~> 1.4"
  gem "jekyll-seo-tag", "~> 2.8"
  gem "jekyll-paginate", "~> 1.1"
  gem "jekyll-redirect-from", "~> 0.16"
  gem "jekyll-archives", "~> 2.2"
end

# Platform-specific gems
gem "wdm", "~> 0.1", :platforms => [:mingw, :mswin, :x64_mingw, :jruby]
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.0" if Gem.win_platform?