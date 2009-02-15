%w[rubygems rake rake/clean fileutils newgem rubigen].each { |f| require f }
require File.dirname(__FILE__) + '/lib/vixploder'
require 'hanna/rdoctask'

$hoe = Hoe.new('vixploder', Vixploder::VERSION) do |p|
  p.developer('Tom Kersten', 'tom@obtiva.com')
  p.changes              = p.paragraphs_of("History.txt", 0..1).join("\n\n")
  p.post_install_message = p.paragraphs_of('PostInstall.txt', 0..10).join("\n\n")
  p.summary              = %q{Tool for simplifying the distribution of environment configuration files ('dotfiles') across multiple *nix-based nodes.}
  p.extra_dev_deps = [
    ['newgem', ">= #{::Newgem::VERSION}"]
  ]

  p.clean_globs |= %w[**/.DS_Store tmp *.log]
  path = (p.rubyforge_name == p.name) ? p.rubyforge_name : "\#{p.rubyforge_name}/\#{p.name}"
  p.rsync_args = '-av --delete --ignore-errors'
end

require 'newgem/tasks' # load /tasks/*.rake
Dir['tasks/**/*.rake'].each { |t| load t }
