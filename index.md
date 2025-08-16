Follow these instructions:

```
# First Run Setup
unless File.exists?('./rbs_goose.yml')
  follow_instruction(File('.claude/commands/rbs_goose/index_initialize.md'))
  return
end

config = Config.load('./rbs_goose.yml')
 
case config.type_annotation_mode
when :inline
  follow_instruction(File('.claude/commands/rbs_goose/index_type_inline.md'))
when :file
  follow_instruction(File('.claude/commands/rbs_goose/index_type_file.md'))
end
```
