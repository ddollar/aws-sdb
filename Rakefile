require 'rubygems'
require 'spec/rake/spectask'
require 'rake/gempackagetask'

Spec::Rake::SpecTask.new

gem_spec = Gem::Specification.new do |s|
  s.name = "aws-sdb"
  s.rubyforge_project = s.name
  s.version = "0.3.1"
  s.platform = Gem::Platform::RUBY
  s.has_rdoc = true
  s.extra_rdoc_files = ["README", "LICENSE"]
  s.summary = "Amazon SDB API"
  s.description = s.summary
  s.author = "Tim Dysinger"
  s.email = "tim@dysinger.net"
  s.homepage = "http://aws-sdb.rubyforge.org"
  s.add_dependency "uuidtools"
  s.require_path = 'lib'
  s.files = %w(LICENSE README Rakefile) + Dir.glob("{lib,spec}/**/*")
end

desc "Open an irb session preloaded with this library"
task :console do
  sh "irb -rubygems -I lib -r aws_sdb.rb"
end

Rake::GemPackageTask.new(gem_spec) do |pkg|
  pkg.gem_spec = gem_spec
end

task :install => [:package] do
  sh %{sudo gem install pkg/#{gem_spec.name}-#{gem_spec.version}}
end
