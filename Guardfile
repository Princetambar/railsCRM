# A sample Guardfile
# More info at https://github.com/guard/guard#readme

guard 'bundler' do
  watch('Gemfile')
end

guard 'passenger' do
  watch(%r{lib/.*\.rb})
  watch(%r{config/.*\.rb})
end

guard 'annotate' do
  watch('db/schema.rb')
  # Uncomment the following line if you also want to run annotate anytime a model file changes
  watch('app/models/**/*.rb')
end

guard 'sass', :output => 'styles' do
  watch(/^sass\/(.*)\/)
end

guard 'compass' do
  watch(%r{^src/(.*)\.s[ac]ss})
end


guard 'livereload' do
  watch(%r{^app/.+\.(erb|haml)$})
  watch(%r{^app/helpers/.+\.rb$})
  watch(%r{^/public/.+\.(css|js|html)$})
  watch(%r{^config/locales/.+\.ym$})
end

guard 'cucumber', :cli => '--drb --format pretty --no-profile'do
  watch(%r{features/.+\.feature})
  watch(%r{features/support/.+})                      { 'features' }
  watch(%r{features/step_definitions/(.+)_steps\.rb}) { |m| Dir[File.join("**/#{m[1]}.feature")][0] || 'features' }
end

guard 'rspec', :cli => "--color --format nested --fail-fast --drb" do
  watch(%r{^spec/(.*)_spec\.rb})
  watch(%r{^app/(.*)\.rb})                           { |m| "spec/#{m[1]}_spec.rb" }
  watch(%r{^lib/(.*)\.rb})                           { |m| "spec/lib/#{m[1]}_spec.rb" }
  watch('config/routes.rb')                          { "spec/routing" }
  watch('app/controllers/application_controller.rb') { "spec/controllers" }
  watch('spec/support/controller_spec_helpers.rb')   { "spec/controllers" }
  watch('spec/factories.rb')                         { "spec/models" }
  watch('spec/spec_helper.rb')                       { "spec" }
end