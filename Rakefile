$LOAD_PATH.unshift File.expand_path('lib', __dir__)
require 'voxpupuli/release/version'

task :default => :dummy

desc 'Dummy rake task'
task 'dummy' do
  puts 'this is a dummy rake task that just prints this line.'
end

begin
  require 'github_changelog_generator/task'
  GitHubChangelogGenerator::RakeTask.new :changelog do |config|
    version = Voxpupuli::Release::VERSION
    config.future_release = "v#{version}" if version =~ /^\d+\.\d+.\d+$/
    config.header = "# Changelog\n\nAll notable changes to this project will be documented in this file."
    config.exclude_labels = %w{duplicate question invalid wontfix wont-fix skip-changelog}
    config.user = 'voxpupuli'
    config.project = 'voxpupuli-release'
  end
rescue LoadError
end
