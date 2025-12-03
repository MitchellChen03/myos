# myos
AI agent in Linux environment

# Complete Step-by-Step Guide to Install MyOS on Linux

## Step 1: Transfer the Project to Linux

You have the project on your Windows machine at `C:\Users\user\myos`. Here are a few ways to get it onto Linux:

### Option A: Using SCP (if you have SSH access to your Linux machine)

Open PowerShell on Windows and run:
```powershell
scp -r C:\Users\user\myos username@your-linux-ip:~/
```

### Option B: Using a USB drive
1. Copy the `C:\Users\user\myos` folder to a USB drive
2. Plug it into your Linux machine
3. Copy it to your home directory:
   ```bash
   cp -r /media/your-usb/myos ~/
   ```

### Option C: Recreate the files manually
Copy each file's contents and create them on Linux using a text editor.

---

## Step 2: Install Prerequisites on Linux

Open a terminal on your Linux machine and run:

```bash
# Update package lists
sudo apt update

# Install Python 3, pip, and venv (if not already installed)
sudo apt install -y python3 python3-pip python3-venv

# Install Tkinter (required for the GUI)
sudo apt install -y python3-tk

# Optional: Install ufw if you want firewall commands to work
sudo apt install -y ufw
```

---

## Step 3: Navigate to the Project Directory

```bash
cd ~/myos
```

Verify the files are there:
```bash
ls -la
```

You should see:
```
README.md
requirements.txt
myos/
```

---

## Step 4: Create a Python Virtual Environment

```bash
python3 -m venv venv
```

This creates an isolated Python environment in a folder called `venv`.

---

## Step 5: Activate the Virtual Environment

```bash
source venv/bin/activate
```

Your prompt should now show `(venv)` at the beginning, like:
```
(venv) user@machine:~/myos$
```

---

## Step 6: Install the Python Dependencies

```bash
pip install -r requirements.txt
```

This installs the OpenAI Python library.

---

## Step 7: Run the Application

```bash
python -m myos
```

---

## Step 8: First-Time Setup

1. **API Key Dialog** - A window will pop up asking for your OpenAI API key
   - Go to https://platform.openai.com/api-keys to get one
   - Paste it into the dialog (it will appear as dots for security)
   - Click OK

2. The key is saved to `~/.myos_config.json` with secure permissions

---

## Step 9: Using the App

1. **Type a command** in the text box, for example:
   - `set up a web server`
   - `install docker`
   - `show disk usage`
   - `update and upgrade the system`

2. **Click "Generate Plan"** - The AI will create an execution plan

3. **Review the plan** in the output log

4. **Click "Execute Plan"** - Confirm when prompted

5. **Watch the output** - Each command's results appear in the log

---

## Running It Again Later

Every time you want to run MyOS:

```bash
cd ~/myos
source venv/bin/activate
python -m myos
```

---

## Quick Reference (All Commands)

```bash
# One-time setup
sudo apt update
sudo apt install -y python3 python3-pip python3-venv python3-tk
cd ~/myos
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Run the app
python -m myos
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| `python3: command not found` | `sudo apt install python3` |
| `No module named tkinter` | `sudo apt install python3-tk` |
| `No module named openai` | Make sure venv is activated, then `pip install -r requirements.txt` |
| GUI doesn't appear | Make sure you're running from a desktop environment (not pure SSH) |
| Commands fail with "permission denied" | Your user needs sudo access |
