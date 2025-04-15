
# VI Editor & File Creation Tools in Linux

## Windows Editors

- Notepad  
- Notepad++

## Linux Editors

**CLI (Command Line Interface):** `vi`, `vim`, `nano`, `ex`  
**GUI (Graphical User Interface):** `gedit`, `gvim`, `picp`, `netit`, `emacs`

---

## 1) cat

The `cat` (concatenate) command allows us to create a file, view contents, concatenate files, and redirect output.

### Create a File

```bash
cat > filename
```

### Create a Hidden File

```bash
cat > .file
```

---

## 2) touch

The `touch` command is the easiest way to create new, empty files (0kb).

### Create a Single Empty File

```bash
touch file1
```

### Create Multiple Empty Files

```bash
touch file1 file2 file3 file4
touch file{1..4}
```

### Create a Hidden Empty File

```bash
touch .hiddenfile
```

---

## Tools to Create Files

- `cat` - Concatenate and create content
- `vim` - Visual Instrument Improved
- `touch` - Create empty file
- `vi` - Visual Instrument
- `nano` - Simple command-line editor

---

## vi (Visual Instrument)

A screen-oriented text editor for Unix.

```bash
vi filename
vi .filename
```

---

## vim (Visual Instrument Improved)

An enhanced version of vi.

```bash
yum install vim-enhanced -y
vim filename
vim .filename
```

---

## nano

Command-line text editor similar to Notepad.

```bash
nano filename
```

---

## Difference Between Vim and Vi

- **Vim**: Supports encryption and is feature-rich.  
- **Vi**: No encryption, simpler.

---

## Modes in Vi/Vim/Gvim

- **Command Mode** – Press `Esc`
- **Insert Mode** – Press `i`, `I`, `A`, `a`, `o`, `O`
- **Ex Mode (Execution Mode)** – Press `:`

### Command Mode

```text
yy      - Copy a line  
3yy     - Copy 3 lines  
p       - Paste below cursor  
P       - Paste above cursor  
4p      - Paste 4 times  
dd      - Delete 1 line  
4dd     - Delete 4 lines  
Shift + G - Go to end of file  
gg      - Go to beginning  
/word   - Search forward  
?word   - Search backward  
n       - Next match  
N       - Previous match  
u       - Undo  
Ctrl + r - Redo  
```

### Cursor Movement in Command Mode

```text
h - left  
j - down  
k - up  
l - right  
```

### Save and Quit

```text
Shift + ZZ - Save and quit  
```

### Insert Mode

```text
i - Insert at cursor  
I - Insert at line start  
a - Append after cursor  
A - Append at line end  
o - Open new line below  
O - Open new line above  
```

### Ex Mode (Command Prefix with `:`)

```bash
:q      # Quit without saving
:q!     # Force quit
:w      # Save
:w!     # Force save
:wq     # Save and quit
:wq!    # Force save and quit (updates timestamp)
:x      # Save and quit
:X      # Encrypt file
:25     # Go to line 25
:set nu # Show line numbers
:set nonu # Hide line numbers
:5d     # Delete line 5
:$d     # Delete last line
:3,6d   # Delete lines 3 to 6
:$      # Move to last line
```

### Search and Replace in Vi

```bash
:%s/old/new/g
```

---

## Find and Replace Without Opening File

```bash
sed -e "s/old/new/g" filename
```
