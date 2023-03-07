# ai.py

Single-file Python script that helps you get answers from ChatGPT API in the command line.

Features:
- Save predefined prompts and refer to them with shortcuts
- Highlight code in the output
- Support one-off query and conversation (coming soon)
- Pass messages through stdin

## Install

Just copy the script to a folder in `$PATH`, like `/usr/local/bin`. You can also change its name to `ai` to get ride of the `.py` extension.

## Usage

Paste your OpenAI API key to `~/.ai_cli_api_key`, or set it in `AI_CLI_API_KEY` environment variable.

For detail usage of the script, please read the description of `./ai.py -h`:

```
usage: ai.py [-h] [-s SYSTEM] [-v] [-d] [--version] [PROMPT]

A simple CLI for ChatGPT API

positional arguments:
  PROMPT                your prompt, leave it empty to run REPL

options:
  -h, --help            show this help message and exit
  -s SYSTEM, --system SYSTEM
                        system message to use at the beginning of the
                        conversation. if starts with @, the message will be
                        located through ~/.ai_cli_prompts.json
  -v, --verbose         verbose mode, show params and role name
  -d, --debug           debug mode, enable logging
  --version             show program's version number and exit
```

### One-off query

Pass the message as the first argument:

```
./ai.py 'hello world'
```

### System message

You can pass a system message to define the behavior for the assistant:

```
./ai.py -s 'You are a proofreader' 'its nice know you'
```

You can also save your predefined system messages in `~/.ai_cli_promots.json`
and refer them with `@` at the beginning.

```
cat ~/.ai_cli_prompts.json
{
  "system": {
    "cli": "As a technology assistant with expertise in command line, answer questions in simple and short words for users who have a high-level background. Provide only one example, and explain as less as possible."
  }
}

./ai.py -s @cli 'MacOS grep and replace a string for all .py files in a folder recursively'
```

### Verbose mode

Add `-v` to print role name and parameters used in the API call.
