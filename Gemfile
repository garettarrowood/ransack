source 'https://rubygems.org'
gemspec

gem 'rake'

rails = ENV['RAILS'] || 'master'
arel  = ENV['AREL']  || 'master'

arel_opts =
  case arel
  when /\// # A path
    { path: arel }
  when /^v/ # A tagged version
    { git: 'git://github.com/rails/arel.git', tag: arel }
  else
    { git: 'git://github.com/rails/arel.git', branch: arel }
  end

gem 'arel', arel_opts

gem 'polyamorous', git: 'git://github.com/activerecord-hackery/polyamorous.git'

case rails
when /\// # A path
  gem 'activesupport', path: "#{rails}/activesupport"
  gem 'activemodel', path: "#{rails}/activemodel"
  gem 'activerecord', path: "#{rails}/activerecord"
  gem 'actionpack', path: "#{rails}/activerecord"
when /^v/ # A tagged version
  git 'git://github.com/rails/rails.git', tag: rails do
    gem 'activesupport'
    gem 'activemodel'
    gem 'activerecord'
    gem 'actionpack'
  end
else
  git 'git://github.com/rails/rails.git', branch: rails do
    gem 'activesupport'
    gem 'activemodel'
    gem 'activerecord'
    gem 'actionpack'
    gem 'rack', github: 'rack/rack'
    gem 'i18n', github: 'svenfuchs/i18n'
  end
end
