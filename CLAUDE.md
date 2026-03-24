# Drupal.org Landing Page Redesign

## Parallelization

Maximize parallel work. Spawn multiple sub-agents in a single message when tasks are independent. Use agent teams for features spanning multiple concerns. Research areas concurrently before implementing. Use background agents for anything that doesn't block the next step.

## Task Tracking (MANDATORY)

ALWAYS use TaskCreate/TaskUpdate (beads) to track work. Create tasks BEFORE starting work. Mark in_progress when beginning, completed when done. The user has requested this repeatedly — it is non-negotiable. Every piece of work should have a corresponding task.

## Commit Discipline

Commit and push after every meaningful change. User shares the ngrok/GitHub Pages link with others — stale deploys are visible. Always `git push origin main` after committing.

## Copy Preservation

NEVER change approved copy/messaging when redesigning layout or CSS. The user iterates carefully on copy. If you need to restructure HTML, preserve all text content exactly. Ask before changing any wording.

## Anti-AI Design Patterns

See `ai-design-tells.md` for full research. Key rules:
- Never use two identical cards side by side
- Vary border-radius across element types
- No uniform section padding
- No gradient text on light backgrounds
- Break grid symmetry deliberately
- Use the brand font (ZT Gatha) for headings

## Brand Guidelines

- Primary font: ZT Gatha (headings), Noto Sans (body)
- Colors: Navy #0a1a3a, Blue #009CDE, Dark Blue #006AA9, Light Blue #CCEDF9
- See `brand-guidelines.md` and `brand-tokens.css` for full spec

## Verification Gates

Before declaring any pixel-perfect work "done", run the verification agent:

```
Agent: verify-pixel-perfect
```

This agent fetches drupal.org's live CSS, compares every property against ours, and returns PASS or FAIL. Do NOT claim completion until it returns PASS. The workflow is:

1. Make fixes
2. Run verify-pixel-perfect agent
3. If FAIL → fix the reported mismatches, go to step 2
4. If PASS → commit, push, mark task complete

## Key URLs

- GitHub Pages: https://grasmash.github.io/drupalorgredux/
- Repo: https://github.com/grasmash/drupalorgredux
- Reference: https://new.drupal.org (header/footer structure)
- Reference: https://windsurf.com (design inspiration)
