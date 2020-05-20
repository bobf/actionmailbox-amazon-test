source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }
ruby '2.6.5'
gem 'aws-sdk-sns'
gem 'rails', github: 'bobf/rails', branch: 'actionmailbox-amazon-ingress'
gem 'sqlite3', '~> 1.4'
gem 'orchestration'
gem 'puma', '~> 4.1'
gem 'bootsnap', '>= 1.4.2', require: false
group :development, :test do
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
end
group :development do
  gem 'listen', '~> 3.2'
  gem 'spring'
  gem 'spring-watcher-listen', '~> 2.0.0'
end
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
