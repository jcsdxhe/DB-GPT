# Dashboard feature walkthrough for PR #3278

These images were captured from the frontend at [8de03431](https://github.com/jcsdxhe/DB-GPT/commit/8de034311e4e57feca99a9c9bfc03dfcb85bcec6).

- The source is the repository's fixed Apple financial demo snapshot (FY2022–FY2024).
- The four-widget layout, English dashboard titles, field labels and literal million-unit suffixes are presentation settings in the demo schema.
- Remaining interface labels are translated in the capture browser for this English walkthrough. The images do not claim that full application localization has shipped.
- API and AI responses use deterministic fixtures. These are workflow illustrations, not a fresh live model or backend validation run.
- Application code and Chinese business-case documentation are unchanged. This branch only hosts PR illustrations.

## Images

1. `01-workspace.png`: visual editor, four aligned KPI/chart widgets and global filters.
2. `02-ai-review.png`: annotations, proposed changes and explicit batch confirmation.
3. `03-publish.png`: fixed snapshots and data-source-following links.

All financial amounts are in USD millions. Public source references remain in the repository's Apple example.

The final captures respect the renderer's seven-row chart minimum. Card bounds were checked for overlap and viewport clipping, and all three images were visually reviewed.
