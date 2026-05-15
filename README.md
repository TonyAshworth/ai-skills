# ai-skills

A personal collection of AI skills for Claude Code and other agentic AI tools.

## Installing Skills

To install and/or update the skills in this repository:

1. Clone the repository to `~/code/tonys-ai-skills`:
   ```bash
   git clone https://github.com/tonyashworth/ai-skills.git ~/code/tonys-ai-skills
   ```

2. Navigate to the repository root:
   ```bash
   cd ~/code/tonys-ai-skills
   ```

3. Run the install script:
   ```bash
   bin/install
   ```

The install script will build all skills from `skills/` into a `dist/` directory.

## Creating a New Skill

To create a new skill, use the `write-a-skill` command in Claude Code, or manually:

1. Create a new directory under `skills/{skill-name}`:
   ```bash
   mkdir skills/{skill-name}
   ```

2. Add a `SKILL.md` file with your skill definition (see existing skills for examples)

3. Run `bin/install` to build and install

Skills are automatically registered in `skills.json` via the build script.

## Discovering Skills

Skills in this repo are automatically registered and discoverable via `find-skills` in Claude Code.

View the current skills registry: [skills.json](./skills.json)
