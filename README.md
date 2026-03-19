# Bugtrace

Bugtrace is a lightweight CLI that helps trace a regression back to the exact commit where it was introduced and then explains why that commit is suspicious.

## What it does

- walks a commit range between a known good commit and a known bad commit
- runs a reproducible command at each candidate commit
- finds the first commit where the command starts failing
- captures commit metadata, diffs, and command output
- generates a plain-English explanation
- can optionally ask an LLM for a deeper explanation

## Quick start

```powershell
python bugtrace.py find `
  --repo D:\path\to\repo `
  --good 1234abcd `
  --bad 5678efgh `
  --command "pytest tests/test_login.py -q" `
  --description "Users get logged out after refresh" `
  --output report.json
```

If you want the `bugtrace` command directly, install it first:

```powershell
python -m pip install -e .
bugtrace find --help
```

## AI explanations

By default, Bugtrace generates a local heuristic explanation from the first bad commit and the failing command output.

You can also enable OpenAI-backed explanations:

```powershell
$env:OPENAI_API_KEY = "your-key"
python bugtrace.py find `
  --repo D:\path\to\repo `
  --good 1234abcd `
  --bad 5678efgh `
  --command "pytest tests/test_login.py -q" `
  --description "Users get logged out after refresh" `
  --ai `
  --model gpt-5-mini
```

## Development

Run tests with:

```powershell
python -m unittest discover -s tests -v
```
"# debuger-ai" 
"# debuger-ai" 
