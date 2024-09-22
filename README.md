# Git Blame - CLI Tool (`gb`)

`Git Blame (gb)` is a powerful CLI tool that helps you analyze the top contributors to any file in a Git repository. This tool automates the `git blame` command and provides enhanced features such as contributor rankings, commit timestamps, and support for both Linux and macOS.

## Features
- **Top Contributors:** Analyze the top contributors to any file in a Git repository.
- **Commit Timestamp:** Display the most recent commit date for each contributor.
- **Cross-Platform:** Supports both Linux and macOS for timestamp conversion.
- **Flexible Input:** Allows input either through command-line arguments or interactive prompts.
- **Configurable Output:** Customize the number of top contributors to display.

## Installation

### Prerequisites:
- Ensure you have Git installed on your system.
- The tool is designed to work with Unix-based systems (Linux, macOS) and requires `bash` or `zsh`.

### 1. Clone the Repository

```bash
git clone https://github.com/brendancopley/git-blame-cli.git
cd git-blame-cli
```

### 2. Make the Script Executable

```bash
chmod +x gb
```

### 3. Add to Your PATH (Optional)

To make the `gb` command available globally, move it to a directory in your system's `PATH`. You can also add a custom directory to your `PATH` and move the script there.

#### Option 1: Move to `/usr/local/bin/`
```bash
sudo mv gb /usr/local/bin/
```

#### Option 2: Move to a Custom `bin` Directory
If you want to use a custom `bin` directory (like `~/bin`), add it to your `PATH`:

```bash
# Create bin directory if not already created
mkdir -p ~/bin
# Move the script
mv gb ~/bin/
# Add to PATH in .zshrc or .bashrc
echo 'export PATH=$PATH:~/bin' >> ~/.zshrc
# Reload .zshrc
source ~/.zshrc
```

## Usage

### Basic Usage
To analyze a file and display the top 3 contributors with their most recent commit dates:

```bash
gb path/to/file
```

### Specify Number of Contributors
To display a custom number of top contributors (e.g., top 5):

```bash
gb path/to/file 5
```

### Example Output:
```bash
$ gb src/main.cpp
Processing file: src/main.cpp
40 contributions by john.doe@example.com (Last commit: 2023-09-01 12:34:56)
35 contributions by jane.smith@example.com (Last commit: 2023-08-28 09:12:34)
25 contributions by alice.johnson@example.com (Last commit: 2023-07-15 17:45:23)
Operation completed successfully.
```

### Cross-Platform Support (macOS & Linux)
The tool automatically detects if it's running on macOS or Linux and adjusts the timestamp conversion process accordingly:
- **Linux**: Uses `date -d @<timestamp>` to convert UNIX timestamps to a human-readable date.
- **macOS**: Uses `date -r <timestamp>` for the same conversion.

### Interactive Mode
If no file path is provided, `gb` will prompt you to enter one interactively:

```bash
gb
```

## First Time Setup
On the first run, the tool automatically configures the `.git-blame-ignore-revs` file to make use of the Git blame ignore functionality. This file will store commit hashes to ignore during the blame analysis.

```bash
$ gb path/to/file
Setting up git blame ignoreRevsFile...
Git blame ignoreRevsFile is now set to .git-blame-ignore-revs
Processing file: path/to/file
Operation completed successfully.
```

## Contribution

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/my-feature`.
3. Commit your changes: `git commit -m 'Add my feature'`.
4. Push to the branch: `git push origin feature/my-feature`.
5. Create a new Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
