# n8n Email Lead Collector

An n8n workflow for collecting publicly visible email addresses from a list of website URLs and exporting the results to a CSV file.

The workflow uses official n8n nodes only. It does not require OAuth, external APIs, or community nodes.

## Overview

This repository provides a lightweight automation flow for:

- Accepting a list of website URLs
- Fetching HTML content from each website
- Extracting email addresses from visible page content
- Removing duplicate and invalid email values
- Exporting the result to `emails.csv`

## Requirements

- n8n v1.94.1 or later
- Local n8n instance or Docker-based n8n runtime
- File write access from the n8n process

## Files

| File | Purpose |
|---|---|
| `email-lead-collector.json` | Importable n8n workflow |
| `demo.gif` | Optional screen recording or usage demo |
| `README.md` | Project documentation |

## Usage

1. Import `email-lead-collector.json` into n8n.
2. Open the first `Set` node.
3. Enter website URLs in the expected list format:

   ```json
   [
     "https://www.djangoproject.com",
     "https://www.python.org",
     "https://www.openai.com"
   ]
   ```

4. Run the workflow.
5. Review the exported file at `./emails.csv`.

## Docker Usage

Run n8n with a mounted output directory:

```bash
docker run -it --rm \
  -v $(pwd)/output:/data \
  -e N8N_EDITOR_BASE_URL=http://localhost:5678 \
  -p 5678:5678 n8nio/n8n
```

When using Docker, set the Save File node path to:

```text
/data/emails.csv
```

## Validation

After running the workflow, validate the output by checking:

- The workflow finishes without node errors
- `emails.csv` is created in the expected directory
- Duplicate email addresses are removed
- The result contains only email-like values

## Troubleshooting

### ENOENT: no such file or directory

This usually means the output directory does not exist or the n8n process cannot write to it.

Recommended checks:

- For local execution, use `./emails.csv`.
- For Docker execution, mount a directory and use `/data/emails.csv`.
- Confirm the directory exists before running the workflow.

### No emails found

Possible causes:

- The target website does not expose email addresses in the page HTML.
- The website renders contact information dynamically with JavaScript.
- The request is blocked or redirected.

Recommended checks:

- Test with a website that clearly displays an email address in the HTML.
- Enable `Always Output Data` for debugging specific nodes.
- Review the HTML response before the extraction step.

## Responsible Use

Use this workflow only for legitimate contact discovery, internal research, or approved outreach workflows. Review applicable privacy, anti-spam, and website terms before using extracted contact data.

## License

This project is released under the [MIT License](https://opensource.org/licenses/MIT).
