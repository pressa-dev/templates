# Pressa document templates

Professionally designed document templates (invoices, purchase orders, packing slips, delivery notes, receipts, reports, certificates, resumes, academic CVs and cover letters, 50 designs in all) you can fill with data and turn into a PDF, by hand, from code, or by asking an AI assistant. Browse them with previews at **[pressa.dev/templates](https://pressa.dev/templates)**.

| Document | Designs (folder) |
|---|---|
| [Invoice](https://pressa.dev/templates/invoice) | Bold ([invoice](invoice)), Classic ([classic-invoice](classic-invoice)), Minimal ([minimal-invoice](minimal-invoice)), Modern ([modern-invoice](modern-invoice)), Corporate ([corporate-invoice](corporate-invoice)) |
| [Purchase order](https://pressa.dev/templates/purchase-order) | Standard ([purchase-order](purchase-order)), Bold ([bold-purchase-order](bold-purchase-order)), Classic ([classic-purchase-order](classic-purchase-order)), Minimal ([minimal-purchase-order](minimal-purchase-order)), Corporate ([corporate-purchase-order](corporate-purchase-order)) |
| [Packing slip](https://pressa.dev/templates/packing-slip) | Standard ([packing-slip](packing-slip)), Bold ([bold-packing-slip](bold-packing-slip)), Classic ([classic-packing-slip](classic-packing-slip)), Minimal ([minimal-packing-slip](minimal-packing-slip)), Corporate ([corporate-packing-slip](corporate-packing-slip)) |
| [Delivery note](https://pressa.dev/templates/delivery-note) | Bold ([delivery-note](delivery-note)), Standard ([standard-delivery-note](standard-delivery-note)), Classic ([classic-delivery-note](classic-delivery-note)), Minimal ([minimal-delivery-note](minimal-delivery-note)), Corporate ([corporate-delivery-note](corporate-delivery-note)) |
| [Cash receipt](https://pressa.dev/templates/cash-receipt) | Framed ([cash-receipt](cash-receipt)), Bold ([bold-cash-receipt](bold-cash-receipt)), Classic ([classic-cash-receipt](classic-cash-receipt)), Minimal ([minimal-cash-receipt](minimal-cash-receipt)), Corporate ([corporate-cash-receipt](corporate-cash-receipt)) |
| [Monthly report](https://pressa.dev/templates/monthly-report) | Standard ([monthly-report](monthly-report)), Bold ([bold-monthly-report](bold-monthly-report)), Executive ([executive-monthly-report](executive-monthly-report)), Minimal ([minimal-monthly-report](minimal-monthly-report)), Corporate ([corporate-monthly-report](corporate-monthly-report)) |
| [Certificate](https://pressa.dev/templates/certificate) | Classic ([certificate](certificate)), Modern ([modern-certificate](modern-certificate)), Minimal ([minimal-certificate](minimal-certificate)), Bold ([bold-certificate](bold-certificate)), Elegant ([elegant-certificate](elegant-certificate)) |
| [Resume](https://pressa.dev/templates/resume) | Classic ([classic-resume](classic-resume)), Modern ([modern-resume](modern-resume)), Banner ([banner-resume](banner-resume)), Sidebar ([sidebar-resume](sidebar-resume)), Elegant ([elegant-resume](elegant-resume)) |
| [Academic CV](https://pressa.dev/templates/academic-cv) | Traditional ([academic-cv](academic-cv)), Classic ([classic-academic-cv](classic-academic-cv)), Modern ([modern-academic-cv](modern-academic-cv)), Elegant ([elegant-academic-cv](elegant-academic-cv)), Timeline ([timeline-academic-cv](timeline-academic-cv)) |
| [Cover letter](https://pressa.dev/templates/cover-letter) | Classic ([cover-letter](cover-letter)), Modern ([modern-cover-letter](modern-cover-letter)), Banner ([banner-cover-letter](banner-cover-letter)), Sidebar ([sidebar-cover-letter](sidebar-cover-letter)), Elegant ([elegant-cover-letter](elegant-cover-letter)) |

Every document comes in five designs, and every design in five colours. The designs of one document take exactly the same data, so you can switch design without changing a field; so do the packing slip and the delivery note. The business documents share design names (Bold, Classic, Minimal, Corporate...), so an invoice, a purchase order and a packing slip can match, and each cover letter matches the resume design of the same name. Send `"color"` next to `data` to print a design in another of the colours its `meta.yml` lists. Long item lists break across pages with the table header repeated.

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
