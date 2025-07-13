## CLI Agents

This project supports the following CLI agents:

- [Goose](https://block.github.io/goose/)
- [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)


The `CONTEXT.md` file serves as the single source of truth for the main system prompt. To accommodate various assistants, several tool-specific files are symbolically linked to it:

- `GEMINI.md` -> `CONTEXT.md`
- `CLAUDE.md` -> `CONTEXT.md`
- `.goosehints` -> `CONTEXT.md`

This means you only need to edit `CONTEXT.md`, and all supported assistants will receive the same core instructions.

## Setup for Specific Assistants

### Windsurf

1.  Rename the `.hc1` directory to `.windsurf`:
    ```bash
    mv .hc1 .windsurf
    ```

### Cursor

1.  First, rename all the rule files to use the `.mdc` extension required by Cursor:
    ```bash
    # This command finds all .md files in .hc1/rules/ and renames them to .mdc
    for f in .hc1/rules/*.md; do mv -- "$f" "${f%.md}.mdc"; done
    ```
2.  Then, rename the directory itself to `.cursor`:
    ```bash
    mv .hc1 .cursor
    ```

## Symlink Requirement on Windows

For symbolic links to work correctly when cloning this repository on Windows, you must have `core.symlinks` enabled in your Git config and have Developer Mode enabled in Windows settings. You can enable it with:

```bash
git config --global core.symlinks true
```
