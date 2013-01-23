require "yaml"

task :default => :build

config = YAML.load File.read "config.yaml"

desc 'Build _site content (all content, default task)'
task :build do
  sh "wlt build"
end

desc 'Build site and deploy'
task :deploy => :build do
  sh "rsync --checksum -rtzh --progress --delete _site/ #{config["deploy_to"]}"
end

