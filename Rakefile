require "bundler/gem_tasks"

desc "Update jQuery-Form-Validator from Git"
task :update do
  BASE = 'jQuery-Form-Validator'
  puts "Update from Git #{BASE} sources"
  if Dir[BASE].none?
    `git clone https://github.com/victorjonsson/jQuery-Form-Validator.git`
  end
  log = `cd #{BASE} && git pull && npm install && ./node_modules/grunt-cli/bin/grunt build`
  if $?.exitstatus
    `mkdir ./app/assets/javascripts 2>&1`
    `mkdir ./app/assets/javascripts/lang 2>&1`
    `mkdir ./app/assets/stylesheets 2>&1`
    `cp #{BASE}/form-validator/*.js    ./app/assets/javascripts/`
    `cp #{BASE}/form-validator/lang/*  ./app/assets/javascripts/lang/`
    `cp #{BASE}/form-validator/*.css   ./app/assets/stylesheets/`
    # `rm -rf #{BASE}`
  else
    puts "Error: #{log}"
  end
end