source "https://rubygems.org"

# Latest Jekyll — built and deployed via GitHub Actions
# (.github/workflows/jekyll.yml), not the classic Pages branch build.
gem "jekyll", "~> 4.4"

# Hacker theme (terminal look)
gem "jekyll-theme-hacker"

# Plugins enabled in _config.yml
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end

# Windows / JRuby timezone data (harmless elsewhere)
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]
