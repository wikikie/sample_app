### Lessons from [Ruby on Rails Tutorial](http://railstutorial.org)
===
####Initialization
1. Run `rails new _project_name_ --skip-test-unit`, if you don't want to use the **Unit::Test**. However, you can still type `rails generate rspec:install` if you want **RSpec** for testing.
2. Modify your Gemfile to group useful gem. Use `bundle install --without production` to avoid future invocation of Bundler for production gems.
3. Modify **config/initializers/secret_token.rb** to make sure the secret token is dynamically generated. And, be sure to make the **.secret** file ignored by **.gitignore**.

```ruby
def secure_token
  token_file = Rails.root.join('.secret')
  if File.exist?(token_file)
    File.read(token_file).chomp
  else
    token = SecureRandom.hex(64)
    File.write(token_file, token)
    token
  end
end
SampleApp::Application.config.secret_key_base = secret_token`
```
