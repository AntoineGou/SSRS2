# SSRS2 - Enterprise RDLC/PDF Engine for .NET

**The modern, cross-platform solution for SSRS Report Viewer — built for enterprise scale.**

Generate pixel-perfect PDFs, Excel, Word, and HTML reports from RDLC files on any platform: Windows, Linux, macOS, Docker, Kubernetes, and cloud environments.

<p align="center">
  <a href="https://ssrs.finctoria.com">
    <img src="https://img.shields.io/badge/Live%20Demo-Try%20It%20Now-success?style=for-the-badge" alt="Live Demo">
  </a>
  <a href="https://tally.so/r/VLPb6J">
    <img src="https://img.shields.io/badge/Contact%20Sales-Request%20Quote-blue?style=for-the-badge" alt="Contact Sales">
  </a>
</p>

---

## Why SSRS2?

Microsoft's legacy Report Viewer is tied to Windows, making it impossible to run in modern cloud-native environments. **SSRS2** solves this with our proprietary cross-platform rendering engine — fully managed, high-performance, and built from the ground up for cloud-native deployments.

### Enterprise-Grade Features

| Feature | SSRS2 | Legacy Report Viewer |
|---------|-----------|---------------------|
| **Linux / Docker / Kubernetes** | ✅ Full support | ❌ Not supported |
| **macOS** | ✅ Full support | ❌ Not supported |
| **Azure App Service (Linux)** | ✅ Full support | ❌ Not supported |
| **AWS Lambda / Fargate** | ✅ Full support | ❌ Not supported |
| **.NET 8 / 9 / 10** | ✅ Native support | ⚠️ Limited |
| **Zero Native Dependencies** | ✅ Self-contained engine | ❌ Requires system libraries |
| **PDF with Hyperlinks** | ✅ Full support | ✅ Supported |
| **Multi-format Export** | ✅ PDF, XLSX, DOCX, HTML, PNG, JPEG | ✅ Similar |
| **Chart Support** | ✅ All chart types | ✅ All chart types |
| **Existing RDLC Compatibility** | ✅ Drop-in replacement | ✅ Native |

---

## Supported Export Formats

- **PDF** — Print-ready documents with embedded fonts and hyperlinks
- **Excel (XLSX)** — Native Open XML spreadsheets
- **Word (DOCX)** — Native Open XML documents
- **HTML5** — Responsive web-ready output
- **PNG / JPEG / WebP** — High-resolution image export

---

## Platform Support

| Platform | Status |
|----------|--------|
| Windows x64 | ✅ Production Ready |
| Linux x64 (Ubuntu, Debian, Alpine) | ✅ Production Ready |
| Linux ARM64 (Graviton, Raspberry Pi) | ✅ Production Ready |
| macOS (Intel & Apple Silicon) | ✅ Production Ready |
| Docker & Kubernetes | ✅ Production Ready |
| Azure App Service | ✅ Production Ready |
| AWS ECS / Lambda | ✅ Production Ready |
| Google Cloud Run | ✅ Production Ready |

---

## Migration Path

SSRS2 is designed as a **drop-in replacement** for Microsoft Report Viewer. Your existing RDLC files work without modification:

```csharp
// Before (Microsoft Report Viewer - Windows only)
using Microsoft.Reporting.WinForms;

// After (SSRS2 - runs anywhere)
using Ssrs2.Reporting;

var report = new LocalReport();
report.LoadReportDefinition(rdlcStream);
report.DataSources.Add(new ReportDataSource("Data", yourData));

byte[] pdf = report.Render("PDF");
```

---

## Enterprise Licensing

SSRS2 is available under a **commercial license** for enterprise use.

### What's Included

- NuGet package with full API access
- Priority support & SLA options
- Custom feature development
- Dedicated onboarding assistance
- License for unlimited developers
- Deployment on unlimited servers

### Industries We Serve

- **Finance & Banking** — Regulatory reports, statements, compliance documents
- **Healthcare** — Patient records, lab reports, insurance claims
- **Manufacturing** — Production reports, quality control, shipping documents
- **Retail & E-commerce** — Invoices, inventory reports, sales analytics
- **Government** — Public records, permits, certificates
- **Insurance** — Policies, claims, actuarial reports

---

## Get Started

### Try the Live Demo

Experience SSRS2 instantly at **[ssrs.finctoria.com](https://ssrs.finctoria.com)** — generate PDF, Excel, Word, and image exports from a sample RDLC report running on Linux.

### Request a Custom Demo

Want to see SSRS2 with your own RDLC files? Our team will demonstrate the migration process and answer your technical questions.

### Contact Sales

Ready to modernize your reporting infrastructure? Our enterprise sales team will work with you to find the right licensing model for your organization.

<p align="center">
  <a href="https://tally.so/r/VLPb6J">
    <img src="https://img.shields.io/badge/Contact%20Sales-Request%20Demo-blue?style=for-the-badge&logo=microsoft" alt="Contact Sales">
  </a>
</p>

---

## Technical Support

| Channel | Purpose |
|---------|---------|
| [GitHub Issues](https://github.com/AntoineGou/rdlcPdf/issues) | Bug reports & feature requests |
| [GitHub Discussions](https://github.com/AntoineGou/rdlcPdf/discussions) | Technical Q&A & community |
| [Enterprise Support](https://tally.so/r/VLPb6J) | Priority support for licensed customers |

---

## About

SSRS2 is developed and maintained by a team with deep expertise in .NET, document processing, and enterprise software. We're committed to providing a reliable, performant, and fully supported solution for organizations migrating away from legacy Windows-only reporting infrastructure.

---

<p align="center">
  <strong>SSRS2</strong> — Enterprise Reporting for the Modern Cloud
</p>

<p align="center">
  <a href="https://ssrs.finctoria.com">Live Demo</a> •
  <a href="https://tally.so/r/VLPb6J">Contact Sales</a> •
  <a href="https://github.com/AntoineGou/rdlcPdf/issues">Report Bug</a> •
  <a href="https://github.com/AntoineGou/rdlcPdf/discussions">Discussions</a>
</p>
