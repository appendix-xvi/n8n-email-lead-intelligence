# n8n Email Lead Intelligence

Work-in-progress n8n automation project for collecting publicly visible contact emails from approved website lists and exporting the results for review.

This repository is not ready for production use yet. The workflow file must exist in the repository before this project should be shared as a completed portfolio item.

## Intended workflow

The planned workflow will:

1. Accept a controlled list of website URLs.
2. Fetch public HTML content from each website.
3. Extract email-like values from visible page content.
4. Remove duplicates and obvious invalid values.
5. Export the reviewed result to CSV.

## Current repository status

```text
Status: work in progress
Ready to showcase: no
```

Before this repository is presented publicly, it needs the actual importable n8n workflow JSON and sample data.

## Required files before showcase

```text
email-lead-collector.json       # importable n8n workflow
samples/input-urls.json         # safe demo input
samples/emails.example.csv      # expected demo output
README.md                       # usage documentation
```

Do not claim these files exist unless they are committed.

## Planned usage

After `email-lead-collector.json` is added:

1. Open n8n.
2. Import `email-lead-collector.json`.
3. Update the input URL list in the first configuration node.
4. Run the workflow.
5. Review the generated CSV output.

## Docker runtime example

```bash
docker run -it --rm \
  -v "$(pwd)/output:/data" \
  -e N8N_EDITOR_BASE_URL=http://localhost:5678 \
  -p 5678:5678 \
  n8nio/n8n
```

When running in Docker, write output files under:

```text
/data
```

## Validation checklist

Before publishing this repository as a finished project, verify:

- The workflow JSON imports into n8n without errors.
- The demo input uses approved public websites only.
- The workflow creates a CSV output.
- Duplicate values are removed.
- The README matches the committed files.
- No private customer, company, or personal data is committed.

## Responsible use

Use this workflow only for legitimate contact discovery, internal research, or approved outreach workflows. Review applicable privacy, anti-spam, and website terms before using extracted contact data.

## License

MIT
