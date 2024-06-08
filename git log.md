The `git log` command in Git is a powerful tool for examining the history of commits in a repository. Here are some commonly used options with examples to help you understand how they work:

### Basic `git log`

```bash
git log
```
This command shows the list of commits in the repository in reverse chronological order.

### Display a One-Line Summary for Each Commit

```bash
git log --oneline
```
This option condenses each commit to a single line, showing the commit hash and commit message.

### Limit the Number of Commits

```bash
git log -n 3
```
This command shows only the last 3 commits.

### Display Commit History for a Specific File

```bash
git log -- <filename>
```
Example:
```bash
git log -- README.md
```
This shows the commit history related to the `README.md` file.

### Show Differences Introduced in Each Commit

```bash
git log -p
```
This command shows the differences (patches) introduced in each commit.

### Format the Log Output

```bash
git log --pretty=format:"%h - %an, %ar : %s"
```
This command customizes the log output. The format placeholders are:
- `%h`: Abbreviated commit hash
- `%an`: Author name
- `%ar`: Author date, relative
- `%s`: Subject (commit message)

### Show Graph of the Branches

```bash
git log --graph
```
This displays an ASCII graph of the branch and merge history next to the commit information.

### Combining Options

You can combine several options to customize the output:
```bash
git log --oneline --graph --decorate --all
```
- `--oneline`: One line per commit
- `--graph`: ASCII graph of the branch structure
- `--decorate`: Adds branch and tag names
- `--all`: Shows all branches

### Filter Commits by Author

```bash
git log --author="Author Name"
```
This shows commits made by a specific author.

### Search for Commits by Commit Message

```bash
git log --grep="search term"
```
This searches for commits with messages containing the given term.

### Show Commits Within a Specific Date Range

```bash
git log --since="2023-01-01" --until="2023-12-31"
```
This displays commits made between January 1, 2023, and December 31, 2023.

### Show Only Merge Commits

```bash
git log --merges
```
This displays only merge commits.

### Example Combining Multiple Filters

```bash
git log --author="Jane Doe" --since="2023-01-01" --until="2023-12-31" --grep="fix" --oneline --graph
```
This command shows a graph of one-line commit summaries for commits by "Jane Doe" in 2023 with commit messages containing "fix".

These options and combinations can be very useful for tailoring the `git log` output to your specific needs, whether you're looking for a high-level overview or detailed information on individual commits.
