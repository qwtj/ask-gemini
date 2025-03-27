# ask-google-gemini

A command-line tool to interact with the Google Gemini API.

## Usage

```bash
ask-google-gemini [-m <model name>] [-g] [-f <attached_File>] [-s] <prompt>
```

### Arguments:

*   `<prompt>`: The text prompt to send to the Gemini API. If `-g` is used, this is the initial prompt.  If a file is piped into the script the prompt will be appended to the end of file.

### Options:

*   `-p <prompt path>`: Provide a path to a file containing the prompt.
*   `-s`: Enable Google Search for the prompt.
*   `-v`: Enable verbose mode.
*   `-h, --help`: Display this help message.
*   `-m <model name>`: Specify the model (e.g., `gemini-2.0-flash`, `gemini-1.5-pro`, etc.).
    *   Supported models: `gemini-2.0-flash`, `gemini-2.0-flash-lite`, `gemini-1.5-flash`, `gemini-1.5-flash-8b`, `gemini-1.5-pro`
*   `-g`: Use `glow` to display the output.
*   `-f <attached_File>`: Path to a file to include in the request.
*   `-i`: List all models along with their details.

## Examples

1.  **Simple Prompt:**

    ```bash
    ask-google-gemini "What is the capital of France?"
    ```

2.  **Prompt with Google Search:**

    ```bash
    ask-google-gemini -s "What are the latest news headlines?"
    ```

3.  **Specify Model:**

    ```bash
    ask-google-gemini -m gemini-1.5-pro "Translate this to Spanish: Hello, world!"
    ```

4.  **Use Glow for Output:**

    ```bash
    ask-google-gemini -g "Explain the concept of quantum entanglement."
    ```

5.  **Attach a File:**

    ```bash
    ask-google-gemini -f ./my_document.txt "Summarize the contents of this file."
    ```

6.  **Read Prompt from File:**

    ```bash
    ask-google-gemini -p ./my_prompt.txt
    ```

7.  **List available models:**

    ```bash
    ask-google-gemini -i
    ```

8.  **Piping a file prompt with additional text**

    ```bash
    cat ./my_prompt.txt | ask-google-gemini "And also answer this prompt."
    ```

## Prerequisites

*   **Google API Key:** You need a Google API key with access to the Gemini API. Set it as an environment variable:

    ```bash
    export GOOGLE_API_KEY="YOUR_API_KEY"
    ```

*   **jq:**  A lightweight and flexible command-line JSON processor.  Install using your operating system's package manager.

    ```bash
    # Example (Debian/Ubuntu)
    sudo apt-get update
    sudo apt-get install jq
    ```

*   **curl:** A command-line tool for making HTTP requests.  It's usually pre-installed on most systems.

*   **base64:** A command-line tool to encode and decode files or strings. It's usually pre-installed on most systems.

*   **glow** (Optional): If you want to use the `-g` option, you need to install `glow`:

    ```bash
    brew install glow
    ```

## Installation

1.  **Clone the repository:**

    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

2.  **Make the script executable:**

    ```bash
    chmod +x ask-google-gemini
    ```

3.  **(Optional) Add to your PATH:**  To make the script accessible from anywhere, add it to a directory in your `PATH` environment variable. For example:

    ```bash
    sudo mv ask-google-gemini /usr/local/bin/
    ```

## Environment Variables

*   `GOOGLE_API_KEY`: Your Google API key. Required.

## Error Handling

The script includes error handling for:

*   Missing or invalid API key.
*   Invalid command-line arguments.
*   File not found.
*   Invalid model name.
*   Empty responses from the API.
*   Network connectivity issues.
*   Missing `jq` or `curl` utilities.

## Notes

*   The script uses temporary files for storing request bodies and responses. These files are automatically cleaned up upon successful execution or when interrupted.
*   Verbose mode (`-v`) can be helpful for debugging, as it displays the API URL, request headers, and saves the request and response to files.
*   The default model is `gemini-2.0-flash`. You can change it using the `-m` option.
*   When attaching files, the script determines the MIME type using the `file` command.  Ensure that the `file` command is available on your system.
*   If a prompt file is specified with `-p`, its contents are read and used as the prompt.
*   If standard input is a pipe or contains content, it is read and appended to the prompt.  If no arguments are passed and standard input is empty, the usage is shown and the script exits.
*   The google search tool will only work if the model supports it.
