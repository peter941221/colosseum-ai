# Colosseum AI - Project Rules

## Preview Process Rule (Hard Requirement)

When any code/content/config file changes, always run this sequence before sharing preview links:

1. Kill previous local preview processes:
   - `taskkill /IM mkdocs.exe /F`
   - `Get-CimInstance Win32_Process | Where-Object { $_.Name -eq 'python.exe' -and $_.CommandLine -match 'mkdocs\\s+serve' } | ForEach-Object { Stop-Process -Id $_.ProcessId -Force }`
2. Start a fresh preview process from project root:
   - `mkdocs serve -a 127.0.0.1:8000`
3. Verify the new process is the only active preview instance.
4. Verify updated page content via HTTP check before reporting completion.
5. Then provide URLs to user:
   - English: `http://127.0.0.1:8000/colosseum-ai/`
   - Chinese: `http://127.0.0.1:8000/colosseum-ai/zh/`

## Content Integrity Rule

- If user provides debate source text, publish it verbatim.
- Do not add extra narrative, style descriptions, or interpretation unless explicitly requested.
