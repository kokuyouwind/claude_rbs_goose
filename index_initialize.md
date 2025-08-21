Follow these instructions:

```
# Setup configurations
file = File.copy('./claude/commands/rbs_goose/rbs_goose.template.yml', './rbs_goose.yml')

puts(file.contents)
until('If there are no problems with the above settings file, please answer yes. If you wish to update the file, please describe the changes.') do
  file.update_contents
end

# Setup tools
config = Config.load('./rbs_goose.yml')
unless gemfile.contain?('rbs')
  puts('setup rbs...')
  fetch('https://github.com/soutaro/steep')
  setup_rbs

  if config.type_annotation_mode.inline?
    fetch('https://github.com/soutaro/rbs-inline')
    setup_rbs_inline
  end

  fetch('https://github.com/ruby/gem_rbs_collection')
  setup_rbs_collection
end

unless gemifle.contain?('steep')
  puts('setup steep...')
  fetch('https://github.com/soutaro/steep')
  setup_steep
  update_steep_config(directory_structure)
end

if rails_app? && !gemfile.contain?('rbs')
  puts('setup rbs-rails...')
  fetch('https://github.com/pocke/rbs_rails')
  setup_rails
end

update_git_ignore <~~GITIGNORE
  .gem_rbs_collection/
  .claude/commands/rbs_goose.md
  .claude/commands/rbs_goose/
GITIGNORE
puts('Initialize Complete!')

case config.type_annotation_mode
when :inline
  follow_instruction(File('.claude/commands/rbs_goose/index_type_inline.md'))
when :file
  follow_instruction(File('.claude/commands/rbs_goose/index_type_file.md'))
end
```