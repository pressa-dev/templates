# Pressa document templates

Professionally designed document templates (invoices, purchase orders, packing slips, receipts, reports, certificates, resumes, cover letters) you can fill with data and turn into a PDF, by hand, from code, or by asking an AI assistant. Browse them with previews at **[pressa.dev/templates](https://pressa.dev/templates)**.

| Template | What it is |
|---|---|
| [invoice](invoice) | Branded invoice, itemised table, totals and tax computed from the data |
| [purchase-order](purchase-order) | Purchase order with vendor and ship-to blocks, totals and tax computed from the data |
| [packing-slip](packing-slip) | Packing slip for the box: item numbers and quantities, no prices |
| [delivery-note](delivery-note) | Delivery note with the same data as the packing slip and lines for the receiver's signature |
| [cash-receipt](cash-receipt) | Cash receipt in the top half of the page, to print and cut |
| [monthly-report](monthly-report) | Business report with KPI cards, a bar chart from your numbers and a metrics table |
| [certificate](certificate) | Landscape certificate with a gold frame and signature lines |
| [classic-resume](classic-resume) | One-page resume, serif typeface, blue section rules |
| [modern-resume](modern-resume) | One-page resume, sans-serif, teal accent, skills table |
| [banner-resume](banner-resume) | Resume with your name in a full-width colour band |
| [sidebar-resume](sidebar-resume) | Two-column resume with a colour sidebar for contact, skills and education |
| [elegant-resume](elegant-resume) | Serif resume with small-caps headings in the margin |
| [academic-cv](academic-cv) | Multi-page academic CV with numbered publications |
| [cover-letter](cover-letter) | Cover letter that matches the classic resume |

The five resume designs (classic, modern, banner, sidebar, elegant) take the same data, so you can switch design without changing a field; so do the packing slip and the delivery note. Designs with a `colors` list in `meta.yml` print in any of those colours: send `"color": "navy"` next to `data`. Long item lists break across pages with the table header repeated.

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
