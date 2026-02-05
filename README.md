# SSRS2 — Cross-Platform RDLC Report Engine for .NET

**Generate pixel-perfect PDFs, Excel, Word, and HTML reports from RDLC files on any platform.**

Drop-in replacement for Microsoft Report Viewer — runs on Windows, Linux, macOS, Docker, Kubernetes, and cloud environments. No GDI+, no `libgdiplus`, no native dependencies.

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
using Ssrs2.Reporting;

var report = new LocalReport();
report.LoadReportDefinition(rdlcStream);
report.DataSources.Add(new ReportDataSource("Data", yourData));

byte[] pdf = report.Render("PDF");
```

Your existing `.rdlc` files work without modification. No code rewrite needed.

> **Free trial** — works without a license key. Output includes a small watermark until activated.  
> Get a license at [ssrs2.net](https://ssrs2.net) or call `Ssrs2.License.Activate("your-key")` to remove it.

---

## Why SSRS2?

Microsoft deprecated ReportViewer for .NET Core and wants everyone on [Power BI Paginated Reports](https://ssrs2.net/ssrs-to-dotnet-core) ($24/user/month). If you have existing RDLC reports and need to run them on modern .NET, your options are limited:

| | SSRS2 | ReportViewerCore (free) | Power BI Paginated |
|---|---|---|---|
| **Linux / Docker** | ✅ Native (SkiaSharp) | ⚠️ Needs libgdiplus | ❌ Cloud only |
| **No GDI+ dependency** | ✅ | ❌ System.Drawing | N/A |
| **.NET 8 / 9 / 10** | ✅ | ✅ | N/A |
| **.NET Framework 4.7.2+** | ✅ | ❌ | N/A |
| **macOS / ARM64** | ✅ | ⚠️ Partial | ❌ |
| **Self-hosted** | ✅ | ✅ | ❌ |
| **Commercial support** | ✅ SLA available | ❌ Community | ✅ Microsoft |
| **Data sovereignty** | ✅ On your infra | ✅ | ❌ Cloud |

---

## Export Formats

| Format | Render String | Extension |
|--------|---------------|-----------|
| PDF (with hyperlinks) | `"PDF"` | .pdf |
| Excel | `"EXCELOPENXML"` | .xlsx |
| Word | `"WORDOPENXML"` | .docx |
| HTML5 | `"HTML5"` | .html |
| PNG | `"PNG"` | .png |
| JPEG | `"JPEG"` | .jpg |
| WebP | `"WEBP"` | .webp |
| CSV | `"CSV"` | .csv |
| XML | `"XML"` | .xml |

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
using Ssrs2.Reporting;

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

- **Unlimited developers** — no per-seat fees
- **Unlimited servers** — no per-deployment fees
- **Revenue-based pricing** — starts at $2,000/year
- **All features included** in every tier

See [ssrs2.net/pricing](https://ssrs2.net/pricing) for details.

---

## Resources

| Resource | Link |
|----------|------|
| 🌐 Website | [ssrs2.net](https://ssrs2.net) |
| 🎮 Live Demo | [ssrs2.net/demo](https://ssrs2.net/demo) |
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
| [Contact Sales](https://tally.so/r/VLPb6J) | Enterprise licensing & support |

---

<p align="center">
  <strong>SSRS2</strong> — Enterprise Reporting for Modern .NET
</p>
