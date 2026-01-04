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
git clone https://github.com/your-org/cosyee-gemini-extensions.git ~/.gemini/extensions/cosyee-extensions

# Move/Link them to the root extensions folder (Gemini looks for folders directly under extensions/)
# Recommended: Create symbolic links or move folders
cd ~/.gemini/extensions
ln -s cosyee-extensions/conductor conductor
ln -s cosyee-extensions/devlog devlog
ln -s cosyee-extensions/pw pw
```

**Windows (PowerShell):**
```powershell
# Directory typically located at C:\Users\<Username>\.gemini\extensions
md $env:USERPROFILE\.gemini\extensions

# Clone
cd $env:USERPROFILE\.gemini\extensions
git clone https://github.com/your-org/cosyee-gemini-extensions.git cosyee-extensions

# Move folders up (Windows symlinks can be tricky without admin rights)
mv cosyee-extensions\conductor .
mv cosyee-extensions\devlog .
mv cosyee-extensions\pw .
```

### 2. Enable Extensions
Gemini requires an explicit enablement file to load extensions.

1.  Locate or create `extension-enablement.json` in your `.gemini/extensions` folder.
    - Path: `~/.gemini/extensions/extension-enablement.json`
2.  Copy the content from `extension-enablement.json.example` into your file.

**Example `extension-enablement.json`:**
```json
{
  "conductor": {
    "overrides": ["*"]
  },
  "devlog": {
    "overrides": ["*"]
  },
  "pw": {
    "overrides": ["*"]
  }
}
```
*Note: The wildcard `"*"` enables the extensions for all projects. You can restrict it to specific paths like `"/Users/yourname/Projects/*"` if preferred.*

### 3. Restart Gemini
Restart your Gemini CLI session to load the new commands.

## Usage
- Type `/conductor` to manage tasks.
- Type `/devlog` to save progress.
- Type `/pw` to start browser automation.
