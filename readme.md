# Gemini CLI

A command-line interface for interacting with the Google Gemini API.  This tool allows you to send text prompts to various Gemini models, optionally including files or enabling Google Search.

## Prerequisites

*   **Google API Key:** You need a Google API key with access to the Gemini API.  Set this in your environment as `GOOGLE_API_KEY`.  For example, in your `.zshrc` or `.bashrc`:

    ```bash
    export GOOGLE_API_KEY="YOUR_API_KEY"
    ```

*   **jq:**  A lightweight and flexible command-line JSON processor.  Install it using your system's package manager (e.g., `brew install jq`, `apt-get install jq`).

*   **curl:** A command-line tool for transferring data with URLs. Usually pre-installed on most systems.

*   **base64:** A command-line tool to encode/decode data using the base64 algorithm. Usually pre-installed on most systems.

*   **(Optional) glow:**  A terminal-based markdown renderer.  Install it if you want pretty-printed Markdown output: `brew install glow` or `go install github.com/charmbracelet/glow/v2@latest`.

## Installation

1.  Download the script (e.g., `ask-google-gemini`).

2.  Make the script executable:

    ```bash
    chmod +x ask-google-gemini
    ```

3.  (Optional) Move the script to a directory in your `PATH` (e.g., `/usr/local/bin`) to make it accessible from anywhere.

## Usage

```
Usage: ./ask-google-gemini [-m <model name>] [-g][-f <attached_File>] <prompt>
  <prompt>: The text prompt to send to the Gemini API.  If -g is used, this is the initial prompt.
  -p <prompt path>     Provide a path to a file prompt.
  -s: Enable Google Search for the prompt.
  -v: Enable verbose mode.
  -h, --help: Display this help message.
  -m <model name>: Specify the model (e.g., gemini-2.0-flash, gemini-1.5-pro, etc.)
  Supported models: gemini-2.0-flash, gemini-2.0-flash-lite, gemini-1.5-flash, gemini-1.5-flash-8b, gemini-1.5-pro
  -g: Use glow to display the output.
  -f <attached_File>:  Path to a file to include in the request.
  -i: List all models along with their details
```

**Examples:**

*   **Basic text prompt:**

    ```bash
    ./ask-google-gemini "Tell me a joke."
    ```

*   **Specify a model:**

    ```bash
    ./ask-google-gemini -m gemini-1.5-pro "Write a short story about a robot detective."
    ```

*   **Use glow for Markdown rendering:**

    ```bash
    ./ask-google-gemini -g "Write a markdown document explaining how to install the Kubernetes CLI."
    ```

*   **Include a file in the request:**

    ```bash
    ./ask-google-gemini -f document.txt "Summarize the contents of the attached file."
    ```

*   **Enable Google Search:**

    ```bash
    ./ask-google-gemini -s "What is the current weather in London?"
    ```

*   **Read prompt from a file:**

    ```bash
    ./ask-google-gemini -p prompt.txt
    ```

*   **Verbose mode for debugging:**

    ```bash
    ./ask-google-gemini -v "Explain the theory of relativity."
    ```

*   **List available models:**

    ```bash
    ./ask-google-gemini -i
    ```

*   **Prompt via standard input:**

    ```bash
    echo "Translate this sentence to French: Hello, world!" | ./ask-google-gemini
    ```

    ```bash
    ./ask-google-gemini "Translate this sentence to French:" < sentence.txt
    ```

## Environment Variables

*   `GOOGLE_API_KEY`: Required. Your Google API key for accessing the Gemini API.

## Error Handling

The script includes error handling for:

*   Missing or invalid API key.
*   jq or curl not installed.
*   Invalid model names.
*   File not found.
*   Invalid JSON responses from the API.
*   Empty responses from the API.

## Notes

*   The script cleans up temporary files (created with `mktemp`) on exit.
*   If no prompt is provided as a command-line argument, the script reads from standard input.
*   The default model is `gemini-2.0-flash`.
*   The `-i` option prints a lot of output. It's useful for understanding the available models and their capabilities, but may be verbose.
*   Remember to handle API keys securely and avoid committing them to version control.
*   Consider using `.gitignore` to exclude files that might contain sensitive information.
*   Writitng git commit using diff **Note: there is no approval** `git commit -e -m "$(git diff HEAD --cached | ask-google-gemini -p ../common-prompts/git-commit.txt)"` 
*   Writitng git commit using status **Note: there is no approval** `git commit  -e -m "$(git status -s | ask-google-gemini -p ../common-prompts/git-commit.txt)"`

## License

This project is open-source and available under the [MIT License](LICENSE).  (Replace with the appropriate license if different.)
