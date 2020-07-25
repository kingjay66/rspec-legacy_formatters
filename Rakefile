require "bundler"
Bundler.setup
Bundler::GemHelper.install_tasks

require "rake"

require "rspec/core/rake_task"
require "rspec/legacy_formatters/version"

require "cucumber/rake/task"
Cucumber::Rake::Task.new(:cucumber)

desc "Run all examples"
RSpec::Core::RakeTask.new(:spec) do |t|
  t.ruby_opts = %w[-w]
end

task :default => [:spec, :cucumber]

task :verify_private_key_present do
  private_key = File.expand_path('~/.gem/rspec-gem-private_key.pem')
  unless File.exist?(private_key)
    raise "Your private key is not present. This gem should not be built without it."
  end
end

task :build => :verify_private_key_present
