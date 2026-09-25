# Pressa document templates

Professionally designed document templates you can fill with data and turn into a PDF, by hand, from code, or by asking an AI assistant. Browse them with previews at **[pressa.dev/templates](https://pressa.dev/templates)**.

| Template | What it is |
|---|---|
| [classic-resume](classic-resume) | One-page resume, serif typeface, blue section rules |
| [modern-resume](modern-resume) | One-page resume, sans-serif, teal accent, skills table |
| [academic-cv](academic-cv) | Multi-page academic CV with numbered publications |
| [cover-letter](cover-letter) | Cover letter that matches the classic resume |

The resume templates take the same data, so you can switch style without changing a field.

## Each template

- `template.tex` - the layout: LaTeX with [Liquid](https://shopify.github.io/liquid/) placeholders such as `{{ name }}` and `{% for job in experience %}`.
- `sample.json` - a complete, valid example of the data it takes.
- `meta.yml` - title, description, and instructions for whoever (or whatever) fills it in.

## Get a PDF

**With an AI assistant.** Connect the Pressa MCP server (`claude mcp add --transport http pressa https://api.pressa.dev/mcp`, or add `https://api.pressa.dev/mcp` in any MCP client) and ask: *"Use the Pressa template modern-resume and fill it with my details."* It lists the templates, asks for what is missing and returns the PDF.

**From code or an automation (n8n, Zapier, a script).** Send the data as JSON:

```bash
curl -X POST https://api.pressa.dev/api/v1/public_templates/modern-resume/render \
  -H "Content-Type: application/json" \
  -d '{"data": { ... same shape as sample.json ... }}'
```

The response has a `pdf_url`. It works without an API key for a few documents a day; a [free key](https://pressa.dev/users/sign_up) gives 50 a month. Values are escaped for you, so text like `R&D` or `50%` is safe. A missing field comes back as a list of what to add. Full reference: [pressa.dev/docs/api](https://pressa.dev/docs/api).

**On your own machine.** Fill the placeholders yourself and compile `template.tex` with `pdflatex` from any TeX distribution.

## License

MIT. Use these templates for anything, including commercial work.
