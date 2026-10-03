# SSRS2 — Cross-Platform RDLC Report Engine for .NET

**Run the RDLC reports you already have on any platform: PDF, Excel, Word, HTML and images, laid out as Microsoft's Report Viewer lays them out.**

Drop-in replacement for the `LocalReport` of Microsoft's Report Viewer — runs on Windows, Linux, macOS, Docker, Kubernetes, and cloud environments. No GDI+ and no `libgdiplus`: on Linux it needs only fontconfig, which most systems have (the official .NET Docker images need `libfontconfig1`, see below).

<p align="center">
  <a href="https://www.nuget.org/packages/SSRS2.NETCore">
    <img src="https://img.shields.io/nuget/v/SSRS2.NETCore?style=for-the-badge&label=NuGet&color=004880" alt="NuGet">
  </a>
  <a href="https://ssrs2.net/demo">
    <img src="https://img.shields.io/badge/Live%20Demo-Try%20It%20Now-success?style=for-the-badge" alt="Live Demo">
  </a>
  <a href="https://ssrs2.net">
    <img src="https://img.shields.io/badge/Website-ssrs2.net-blue?style=for-the-badge" alt="Website">
  </a>
</p>

---

## Quick Start

```bash
dotnet add package SSRS2.NETCore
```

```csharp
using SSRS2.Reporting.NETCore;

var report = new LocalReport();
report.LoadReportDefinition(rdlcStream);
report.DataSources.Add(new ReportDataSource("Data", yourData));

byte[] pdf = report.Render("PDF");
```

Your existing `.rdlc` files work without modification, and your `LocalReport` code keeps working once its namespace is changed.

In a Linux container, add fontconfig, which the official .NET images lack:

```dockerfile
RUN apt-get update && apt-get install -y --no-install-recommends libfontconfig1 && rm -rf /var/lib/apt/lists/*
```

> **Free trial** — works without a license key. Output includes a small watermark until activated.  
> Buy a licence at [ssrs2.net/pricing](https://ssrs2.net/pricing): the key arrives by email within a minute. Set it as the `SSRS2_LICENSE` environment variable or call `Ssrs2.License.Activate("your-key")`.

> **Try it in the browser** — the [online designer](https://designer.ssrs2.net/designer?utm_source=github) (beta) opens your `.rdlc`, previews it as SSRS2 renders it on Linux and exports PDF, Excel or Word. No install; an account is only needed to save reports online.

---

## Why SSRS2?

Microsoft's Report Viewer runs on .NET Framework and Windows only: Microsoft declined to port it to .NET Core and points to [Power BI paginated reports](https://ssrs2.net/ssrs-to-dotnet-core) instead (from $14 per viewer per month). If you have existing RDLC reports and need to run them on modern .NET, your options are limited:

| | SSRS2 | ReportViewerCore (free) | Power BI Paginated |
|---|---|---|---|
| **Linux / Docker** | ✅ PDF and images included (with `libfontconfig1`) | ⚠️ HTML, Excel, Word; PDF and images rely on Windows font measurement | ❌ Cloud only |
| **No GDI+ dependency** | ✅ | ❌ System.Drawing | N/A |
| **.NET 8 / 9 / 10** | ✅ | ✅ | N/A |
| **.NET Framework 4.7.2+** | ✅ | ❌ | N/A |
| **macOS / ARM64** | ✅ | ⚠️ Partial | ❌ |
| **Self-hosted** | ✅ | ✅ | ❌ |
| **Support** | Sold separately | Community | Microsoft |
| **Data sovereignty** | ✅ On your infra | ✅ | ❌ Cloud |

---

## Export Formats

| Format | Render String | Extension |
|--------|---------------|-----------|
| PDF (with hyperlinks) | `"PDF"` | .pdf |
| Excel | `"EXCELOPENXML"` | .xlsx |
| Word | `"WORDOPENXML"` | .docx |
| HTML5 | `"HTML5"` | .html |
| HTML 4.0 | `"HTML4.0"` | .html |
| MHTML | `"MHTML"` | .mhtml |
| PNG | `"PNG"` | .png |
| JPEG | `"JPEG"` | .jpg |
| WebP | `"WEBP"` | .webp |
| TIFF (all pages) | `"IMAGE"` | .tif |
| CSV | `"CSV"` | .csv |
| XML | `"XML"` | .xml |

---

## Beyond rendering

- **Check a report without running it:** `report.CheckDefinition()` returns each problem of a definition (its code, item, property and expression), without rendering it.
- **Reports your application did not write:** `RestrictedCode = true` holds their expressions and custom code to what a report computes with: no files, environment, processes or reflection (.NET 8, 9 and 10).
- **PDF settings:** the report's title and author, passwords and permissions (AES-256), or PDF/A-2b for archives.
- **A viewer of your own:** `Toggle`, `Sort`, `FindBookmark`, `FindDocumentMapNode` and `Drillthrough` do what Report Viewer's control does on a click.
- **AI coding agents:** `dnx SSRS2.Mcp` gives Claude Code, Cursor or VS Code tools that check and preview the reports they write, on your machine ([SSRS2.Mcp](https://www.nuget.org/packages/SSRS2.Mcp)).

---

## Platform Support

| Platform | Status |
|----------|--------|
| Windows x64 | ✅ |
| Linux x64 and ARM64 (Debian, Ubuntu, RHEL, Alpine) | ✅ |
| macOS (Intel & Apple Silicon) | ✅ |
| Docker & Kubernetes (Linux containers) | ✅ |
| Azure App Service, AWS ECS, Google Cloud Run | ✅ wherever those containers run |

### .NET Framework Support

| Framework | Status |
|-----------|--------|
| .NET Framework 4.7.2 | ✅ |
| .NET Framework 4.8 | ✅ |
| .NET 8.0 (LTS) | ✅ |
| .NET 9.0 | ✅ |
| .NET 10.0 | ✅ |

---

## Migration from Microsoft ReportViewer

```csharp
// Before (Microsoft Report Viewer — Windows only)
using Microsoft.Reporting.WinForms;

// After (SSRS2 — runs anywhere)
using SSRS2.Reporting.NETCore;

// Same API. Same RDLC files. Any platform.
var report = new LocalReport();
report.LoadReportDefinition(rdlcStream);
report.DataSources.Add(new ReportDataSource("Data", yourData));
byte[] pdf = report.Render("PDF");
```

**Migrate at your own pace** — SSRS2 supports .NET Framework 4.7.2/4.8 AND .NET 8/9/10. Adopt on your existing .NET Framework app today, move to .NET 10 when ready.

📖 [Full migration guide with cost comparison →](https://ssrs2.net/ssrs-to-dotnet-core)

---

## Licensing

SSRS2 is a commercial product with a **free trial** (watermarked output).

- **One licence per company: USD 799 a year, or USD 1,999 for three years** — no per-seat or per-server fees
- **Unlimited developers, applications, servers and renders**: nothing is counted, and the key is checked offline
- **All features included** in every licence, with every release published while it runs; a key keeps working forever with those releases
- **Not included**: support, migration help and custom work (sold separately), and shipping SSRS2 inside software other companies install (a separate redistribution licence)

Buy online at [ssrs2.net/pricing](https://ssrs2.net/pricing); the [licence terms](https://ssrs2.net/terms) are one page.

---

## Resources

| Resource | Link |
|----------|------|
| 🌐 Website | [ssrs2.net](https://ssrs2.net) |
| 🎮 Live Demo | [ssrs2.net/demo](https://ssrs2.net/demo) |
| 🎨 Online Designer (beta) | [designer.ssrs2.net](https://designer.ssrs2.net/designer?utm_source=github) |
| 📖 Migration Guide | [ssrs2.net/ssrs-to-dotnet-core](https://ssrs2.net/ssrs-to-dotnet-core) |
| 📊 Feature Comparison | [ssrs2.net/compare](https://ssrs2.net/compare) |
| 💰 Pricing | [ssrs2.net/pricing](https://ssrs2.net/pricing) |
| 📝 Medium Article | [SSRS to .NET Core: 3 Options Compared](https://medium.com/@ago-m/ssrs-to-net-core-your-3-migration-options-compared-1cc666b5bd56) |
| 📦 NuGet | [nuget.org/packages/SSRS2.NETCore](https://www.nuget.org/packages/SSRS2.NETCore) |

---

## Support

| Channel | Purpose |
|---------|---------|
| [GitHub Issues](https://github.com/AntoineGou/SSRS2/issues) | Bug reports & feature requests |
| [ssrs2.net](https://ssrs2.net) | Documentation & demos |
| [sales@ssrs2.net](mailto:sales@ssrs2.net) | Licences, and support or migration help (sold separately) |

---

<p align="center">
  <strong>SSRS2</strong> — Enterprise Reporting for Modern .NET
</p>
