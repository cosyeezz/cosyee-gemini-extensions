# Cosyee Gemini Extensions

Collection of custom extensions for the Gemini CLI agent, tailored for the Cosyee development workflow.

## Included Extensions

| Extension | Command | Description |
| :--- | :--- | :--- |
| **Conductor** | `/conductor` | Project management, task tracking, and plan execution. |
| **DevLog** | `/devlog` | Automatic development logging and summarization. |
| **Playwright** | `/pw` | E2E browser automation setup, generation, and execution. |

## Installation

### 1. Clone the Repository
Clone this repository into your Gemini extensions directory.

**macOS / Linux:**
```bash
# Create directory if not exists
mkdir -p ~/.gemini/extensions

# Clone into the extensions folder
git clone https://github.com/cosyeezz/cosyee-gemini-extensions.git ~/.gemini/extensions/cosyee-extensions

# Link them to the root extensions folder (Gemini looks for folders directly under extensions/)
cd ~/.gemini/extensions
ln -s cosyee-extensions/conductor conductor
ln -s cosyee-extensions/devlog devlog
ln -s cosyee-extensions/pw pw
```

**Windows (PowerShell):**
```powershell
# Directory typically located at C:\Users\<Username>\.gemini\extensions
if (!(Test-Path $env:USERPROFILE\.gemini\extensions)) { md $env:USERPROFILE\.gemini\extensions }

# Clone
cd $env:USERPROFILE\.gemini\extensions
git clone https://github.com/cosyeezz/cosyee-gemini-extensions.git cosyee-extensions

# Move/Copy folders up (Gemini looks for folders directly under extensions/)
cp -r cosyee-extensions\conductor .
cp -r cosyee-extensions\devlog .
cp -r cosyee-extensions\pw .
```

### 2. Enable Extensions
Gemini requires an explicit enablement file to load extensions.

1.  Locate or create `extension-enablement.json` in your `.gemini/extensions` folder.
    - Path: `~/.gemini/extensions/extension-enablement.json`
2.  Add the following configuration:

```json
{
  "conductor": { "overrides": ["*"] },
  "devlog": { "overrides": ["*"] },
  "pw": { "overrides": ["*"] }
}
```

### 3. Restart Gemini
Restart your Gemini CLI session to load the new commands.

## Usage
- Type `/conductor` to manage tasks.
- Type `/devlog` to save progress.
- Type `/pw` to start browser automation.
