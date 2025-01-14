# HTML to Text Converter (`htmltotext`)

This is a simple Bash script to convert HTML content into plain text by removing HTML tags, CSS content, and decoding HTML entities. It is lightweight and supports input redirection for easy usage in Linux environments.

---

## Features
- Removes all HTML tags and inline CSS content.
- Decodes common HTML entities (e.g., `&lt;`, `&gt;`, `&amp;`).
- Supports input redirection, making it easy to process files directly from the command line.
- Can be added to your `PATH` for terminal-wide usage.

---

## Installation

### Step 1 : Clone or Copy the Script
Copy the script into a file named `htmltotext` and make it executable :
```bash
chmod +x htmltotext
```

### Step 2 : Add to Your `PATH`
If you are on a shared system or don’t have root access, you can add the directory containing the script to your `PATH`.

1. Move the script to a directory like `~/bin` :
   ```bash
   mv htmltotext ~/bin
   ```
2. Add `~/bin` to your `PATH` if it's not already included. Edit your `~/.bashrc`, `~/.bash_profile` or `~/.profile` :
   ```bash
   nano ~/.bashrc
   ```
   Add the following line :
   ```bash
   export PATH="$HOME/bin :$PATH"
   ```

   Or do it in 1 step with :
   ```bash
   echo 'export PATH="$PATH :$HOME/bin"' >> ~/.bashrc
   ```
3. Reload the shell configuration :
   ```bash
   source ~/.bashrc
   ```

---

## Usage

### Basic Usage
To process an HTML file and output plain text to the terminal :
```bash
cat input.html | htmltotext
```

To process an HTML file and output plain text to a file :
```bash
htmltotext < input.html > output.txt
```

### Using Pipes
You can use it with other commands via pipes :
```bash
curl http://example.com | htmltotext > output.txt
```

### Example
Input (`example.html`) :
```html
<h3>Hello, World!</h3>
<p>&lt; This is an example &gt;</p>
```

Command :
```bash
htmltotext < example.html
```

Output :
```plaintext
Hello, World!
< This is an example >
```

---

## Purpose
The `htmltotext` program was designed to help users convert HTML files into plain text efficiently, removing unnecessary tags, CSS, and encoded entities. It is lightweight and ideal for quick text extraction on Linux systems.

I originally made it because I save some webpages locally to view out of convenience, but when I ported my files to a linux server, I was unable to live preview the html and pdf prints of the pages. This tool allowed me to "preview" my html files (which consisted almost **entirely** of text) without having to look at the annoying html tags so I could still have a clean view of its contents. This tool is best suited for processing sites with a lot of textual content, as it does not currently support extracting href links or image data.
