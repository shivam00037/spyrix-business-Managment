# One-page invoice export and workspace themes

## Invoice export
- Invoice Designer export measures the invoice canvas and scales it into a single selected paper size/orientation, printing the invoice canvas only.
- Saved invoice Print / Save PDF output measures and fits its generated invoice sheet to one page.
- Template Studio's Download PDF action also measures and fits its invoice preview to one A4 portrait page.
- The invoice document keeps its selected/saved template styling; compaction rules are print-only and do not change the on-screen template.

## Workspace themes
- Black & White (`mono`) is the default for a fresh or invalid theme state.
- Valid selected themes remain persisted in local storage: Black & White, Neon Yellow & Black, Burgundy, Red & White, Yellow & White, and Purple & White.
- Reference dashboard structure is now shared across palettes; accent colours apply to active navigation, selected tabs/filters, page icons, key actions, progress bars and editor controls.
- Workspace theme changes do not recolour the invoice document itself, so the selected invoice template remains intact.

## Run
From the project root:

```powershell
npm install
npm run dev
```

Use the browser Print dialog and select Save as PDF. The app sets the paper size and scales supported invoice export paths to a single sheet. Use A4 for the usual invoice page; paper-size/orientation settings are respected in Invoice Designer.
