# Installing ArchView

There are many AI apps or channels for you to install an AI skill. Pick whichever of these matches how you use AI.

Here are some for your reference.

## Claude AI

#### Claude app or claude.ai

See the README.md

#### In Claude Code

1. Unzip `archview.zip`.
2. Copy the `archview` folder into your skills directory:
  - Personal (all your projects): `~/.claude/skills/archview`
  - Project-only: `.claude/skills/archview` inside your repo
3. Start a new Claude Code session. Claude will discover and use the skill automatically, no upload step needed.

#### Via Claude API

1. Upload the skill through the `/v1/skills` endpoint to get a `skill_id`.
2. Reference that `skill_id` in the `container.skills` parameter of a Messages API call, alongside the code execution tool. For example:

```python
import anthropic
client = anthropic.Anthropic()

response = client.beta.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=4096,
    betas=["code-execution-2025-08-25", "skills-2025-10-02"],
    container={
        "skills": [
            {"type": "custom", "skill_id": "YOUR_ARCHVIEW_SKILL_ID", "version": "latest"}
        ]
    },
    tools=[{"type": "code_execution_20250825", "name": "code_execution"}],
    messages=[
        {"role": "user", "content": "Create an architecture view for my order processing system"}
    ],
)
```

Custom skills uploaded via the API are shared across your whole workspace.

## ChatGPT (OpenAI)

#### ChatGPT web/desktop

If you have an eligible ChatGPT workspace:
1. Open ChatGPT.

2. Open Plugins in the sidebar.

3. Open Plugin Directory → Skills.

4. Select Create → Upload from your computer.

5. Select the archview.zip.

6. Wait for the security scan.

7. Install it.

For a personal Plus account: if you don't see Skills, there isn't currently a command-line workaround that installs a personal Skill into the ChatGPT UI. Use Codex or the API instead.

#### Codex CLI 

For a local Skill, this is probably the option you want. Codex CLI uses the Agent Skills format, so you can install the Skill into the appropriate Codex Skills directory rather than uploading it to the API.

First install/update Codex:

```
npm install -g @openai/codex
```

Then authenticate:

```
codex --login
```

Install the ArchView Skill (archview.zip). Create the Codex Skills directory if necessary:

```
mkdir -p ~/.codex/skills
```

Unzip the archview.zip there:

```
unzip -q archview.zip -d ~/.codex/skills/
```

#### Codex app

The Codex app uses the same general Skills ecosystem.

```
mkdir -p ~/.codex/skills
unzip -q archview.zip -d ~/.codex/skills/
```

#### OpenAI API 

This is the other good option if you want your Skill to be managed centrally and used by an API application.
Set your API key:

```
export OPENAI_API_KEY="sk-..."
```

Then upload the ZIP:

```
curl https://api.openai.com/v1/skills \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -F "files=@archview.zip"
```

The Skills API supports creating a Skill from a directory upload or a single ZIP file. (OpenAI Developers)
The response will contain something like:

```
{
  "id": "skill_abc123",
  "name": "archview",
  "default_version": "...",
  "latest_version": "..."
}
```

Save the id, something like: skill_abc123. That's the Skill ID your API application can reference.

- List Skills

```
curl https://api.openai.com/v1/skills \
  -H "Authorization: Bearer $OPENAI_API_KEY"
```

- Get a Skill

```
curl https://api.openai.com/v1/skills/skill_abc123 \
   -H "Authorization: Bearer $OPENAI_API_KEY"
```

- Delete a Skill

```
curl -X DELETE \
	https://api.openai.com/v1/skills/skill_abc123 \
 	-H "Authorization: Bearer $OPENAI_API_KEY"
```

## Gemini AI

In the Gemini ecosystem, the mechanism to publish a custom capability or tool depends on whether you are targeting everyday consumer/workspace users or developer interfaces like the Gemini CLI.

#### Gemini CLI / AI Studio

1. Open your terminal in the directory where your project or extension resides.
2. Run the CLI import command pointing to your `archview.zip` file:

```
gemini skills install ./archview.zip
```

Usage: Activate the skill in your prompt or call it directly:

```
gemini --skill skill-name "Run your request here"
```

#### Gemini Web / Custom Extension Interface

If you are using the Gemini Web UI or an extension manager UI:

1. Log in to your Gemini Workspaces / Extensions dashboard.
2. Navigate to Settings > Extensions / Skills.
3. Click Upload Custom Skill (or Import Skill).
4. Select `archview.zip` from your file browser and click Confirm.
5. Ensure the toggle next to your newly installed skill is turned ON.
6. Usage: In the chat bar, type `@archview` followed by your prompt.

#### Python API / SDK Project Integration

If you are developing a local app using the `google-generativeai` package, unpack the skill directly into your project directory to register its function calling definitions:

Unzip `archview.zip` into your project's `./skills` directory:

```
unzip archview.zip -d ./skills/
```

Load and register the unzipped skill modules within your Python code:

## Other AI Tools

Installing a `archview.zip` across modern AI tools (Cursor, Pi, Windsurf, Roo Code, OpenCode, etc.) follows a consistent standard: unpacking the `.zip` so that a folder containing `SKILL.md` rests in the tool's designated skills folder.

### Cursor (IDE)

Cursor supports both global and project-level skills.  

- Global (All Projects): `~/.cursor/skills/`  
- Project-Level (This Repo Only): `<project-root>/.cursor/skills/`

Menu / GUI Option:

1. Open your project in Cursor.
2. In the file explorer, create a folder named `.cursor` at the root, and a `skills` subfolder inside it (e.g., `.cursor/skills/`).  
3. Extract `archview.zip` directly into that `skills/` folder so it looks like `.cursor/skills/archview/SKILL.md`.  
4. Reload Cursor (`Ctrl+Shift+P` / `Cmd+Shift+P` > *Developer: Reload Window*).

### Pi  Coding Agent (CLI)

Pi implements the standard *Agent Skills* directory model.  

- Global: `~/.pi/agent/skills/` or `~/.agents/skills/`
- Project-Level: `<project-root>/.pi/skills/`  

Command Line:

```
# Global installation:
mkdir -p ~/.pi/agent/skills && unzip archview.zip -d ~/.pi/agent/skills/

# Project-level installation:
mkdir -p .pi/skills && unzip archview.zip -d .pi/skills/
```
Interactive Menu Command:

If running Pi interactively, load or toggle skills via the settings menu:

- Type `/settings` inside Pi > Toggle `enableSkillCommands` or verify loaded paths.  
- You can explicitly trigger the skill using `/skill:archview`.  

### Windsurf (Editor / Cascade)

Windsurf stores skills in project or global settings directories.  

- Global: `~/.codeium/windsurf/skills/`
- Project-Level: `<**project-root>/.windsurf/skills/` 

Command Line:

```
# Project-level (Recommended):
mkdir -p .windsurf/skills && unzip archview.zip -d .windsurf/skills/

# Global:
mkdir -p ~/.codeium/windsurf/skills && unzip archview.zip -d ~/.codeium/windsurf/skills/
```

Menu Option:

1. Open the Cascade panel in Windsurf.  
2. Click the `...` (three dots) in the top-right corner > Select Skills.  
3. Click + Workspace or + Global to open the target folder.  
4. Unzip your `archview.zip` contents into that folder.
