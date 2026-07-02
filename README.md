# 8D Report Processor

> A TRAE WORK skill for 8D problem-solving report review and translation, built for quality engineering professionals in manufacturing.

[中文文档](./README_CN.md)

---

## What It Does

This skill processes 8D (Eight Disciplines) problem-solving reports in two modes:

| Mode | Function | Output |
|------|----------|--------|
| **Audit Mode** | Reviews 8D reports against D1-D8 industry standards, identifying missing information, logic flaws, and terminology errors | Word document with issue list and correction suggestions |
| **Translate Mode** | Translates finalized 8D reports between Chinese and English using industry-specific terminology dictionaries | Translated document preserving original format, data, and layout |

The skill automatically detects user intent from keywords and switches to the appropriate mode. When intent is ambiguous, it defaults to Audit Mode and offers translation afterward.

## Supported Industries

The skill includes built-in terminology dictionaries and audit checklists for four major manufacturing sectors:

1. **Automotive Supply Chain** - injection molding, stamping, wire harnesses, air leakage, dimensional tolerance, PFMEA/MSA/PPAP, fixtures, jigs, abnormal noise, coating defects
2. **Consumer Electronics** - main boards, FPC, camera modules, dispensing, cold solder joints, ESD, drop testing, assembly gaps, battery swelling
3. **Electronics / PCB** - PCB short/open circuits, solder balls, component shift, impedance, EMC, connectors, withstanding voltage tests
4. **LCD/OLED Display Panels** - bright dots, dark dots, Mura, light leakage, image retention, color shift, FOG/COG bonding, polarizers, backlight modules, cutting chipping, liquid crystal bubbles

## Key Features

### Audit Mode
- Validates all 8D sections (D1-D8) against industry standards
- Detects three problem categories: missing information, logic flaws, terminology/text issues
- Checks both Chinese reports (vague language, inconsistent terms, lack of quantification) and English reports (grammar, tense, terminology, title standards)
- Flags cross-industry terminology misuse (e.g., display panel terms in an automotive report)
- Generates a structured Word report with compliance rating, issue summary table, per-issue correction suggestions, and common rejection patterns

### Translate Mode
- Uses fixed standard English titles for all D1-D8 sections
- Automatically detects the source document's industry and applies the matching terminology set consistently
- Preserves all numbers, batch IDs, part numbers, defect quantities, timestamps, tables, images, and original layout
- Produces professional manufacturing-grade English/Chinese suitable for foreign enterprise SQE review


```

### Mode Switching

The skill detects mode from your message keywords:

| Keywords | Mode |
|----------|------|
| audit, review, check, inspect, issues, compliance, 审核, 校验, 检查, 整改 | Audit Mode |
| translate, English version, Chinese version, 翻译, 中英互译, 译文 | Translate Mode |

If both are mentioned or intent is unclear, Audit Mode runs first. After completing the audit, the skill will ask whether you need a translation.

## Output

### Audit Mode Output
A Word document containing:
1. **Report Overview** - identified industry, language type, compliance rating (Pass / Needs Revision / Severely Deficient)
2. **Issue Summary Table** - index, D-section, problem type (missing/logic/terminology), description
3. **Per-Issue Correction Suggestions** - specific fixes with standard industry terminology
4. **Common Pitfalls** - frequently rejected issues by industry client auditors

### Translate Mode Output
A translated 8D document in the same format as the original upload (PDF/Word/PowerPoint), with all images, tables, and layout preserved.

## File Structure

```
8d-report-processor/
├── SKILL.md          # Skill definition (YAML frontmatter + rules)
├── README.md         # This file (English)
└── README_zh.md      # Chinese documentation
```

## Technical Details

- **Skill Name**: `8d-report-processor`
- **MCP Dependency**: File System (for reading PDF/Word/TXT/MD/PPT attachments)
- **Supported Input Formats**: Plain text, PDF, Word (.docx), PowerPoint (.pptx), TXT, Markdown
- **Supported Languages**: Chinese (Simplified), English
- **D1-D8 Standard**: Based on automotive industry 8D methodology, adapted for four manufacturing sectors

## Limitations

- Audit Mode does not perform translation; it only reviews and suggests corrections
- Translate Mode does not audit; it assumes the source document is finalized
- The skill does not fabricate 8D content; it only processes what the user provides
- If the source document has obvious logic gaps or missing data, Translate Mode will suggest completing an audit first

## License

This project is intended for personal and professional use in quality engineering workflows.

## Contributing

If you find terminology errors or want to add support for additional manufacturing industries, feel free to submit issues or pull requests.
