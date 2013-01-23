# A sample Guardfile
# More info at https://github.com/guard/guard#readme

guard 'rake', :task => 'build' do
  # layouts
  watch %r{^_layouts/(.+)\.haml$}
  # posts
  watch %r{^_posts/(.+)\.md$}
  # pages
  watch %r{^([^/]+)\.md$}
  # Extra haml files, like atom
  watch %r{^([^/]+)\.haml}
  # Style
  watch %r{^css/(.+)\.sass$}
  # Coffee
  watch %r{^js/mickey\.coffee$}
  # Script
  watch %r{^Rakefile$}
  # Config
  watch %r{config.yaml$}
end
