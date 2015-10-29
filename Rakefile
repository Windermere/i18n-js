require "bundler"
Bundler::GemHelper.install_tasks

require "spec_js/rake_task"
SpecJs::RakeTask.new do |t|
  t.env_js = false
end

require "rspec/core/rake_task"
RSpec::Core::RakeTask.new(:"spec:ruby")

desc "Run all specs"
task :spec => [:"spec:ruby", :"spec:js"]

require "bundler/gem_tasks"

module Bundler
  class GemHelper
    def rubygem_push(path)
      gem_server_url = ENV['GEM_SERVER_URL']
      sh("gem inabox '#{path}' --host #{gem_server_url}")
      Bundler.ui.confirm "Pushed #{name} #{version} to #{gem_server_url}"
    end
  end
end
