rbs-goose Command
=================

You are executing the rbs-goose custom command for Claude Code.

## Usage

This command can be installed via [claude-cmd](https://github.com/kiliczsh/claude-cmd).

```
$ ccmd install kokuyouwind/claude_rbs_goose
# or specify version
$ ccmd install kokuyouwind/claude_rbs_goose@v0.1.0
```

## Command Instructions

When this command is invoked via `/rbs-goose`, you should:

1. If the configuration file is not set up, generate `rbs_goose.yml`.
2. If tools such as steep or rbs_rails are not set up, set them up.
3. Run type checking.
4. Automatically fix type errors.
