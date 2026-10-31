---
name: reclaim
description: Audit local disk use, obsolete software, generated files, and storage growth. Invoke manually for an evidence-based report with targeted cleanup and prevention options; do not perform cleanup during the audit.
---

# Reclaim

Run a manual, read-only storage audit. Find what occupies space, why it exists, whether it is still required, and what prevents repeated growth. Return a report. Do not equate a large folder or an old timestamp with waste.

## Scope and boundaries

- Use the user's requested machine or project scope. For a whole-machine request, inspect local volumes, common user folders, developer projects, application data, and background services. For a project request, inspect its dependencies and output plus relevant shared stores; do not expand into unrelated personal files.
- Do not delete, move to Trash, uninstall, prune, upgrade, edit configuration, stop or start services, empty Trash, or install automation. A later cleanup request is a separate action, not part of invoking this audit.
- Use installed inspection tools. Do not install a scanner, run builds, download dependencies, or execute project scripts just to measure storage.
- Keep inspection local. Verify the active container endpoint before any container query. Do not contact a remote daemon or inspect production settings unless the user requests that scope.
- List blocked paths and stopped services as coverage gaps. Do not bypass permissions or start a stopped runtime to complete the report.
- Read metadata and manifests before file contents. Do not print credentials, private keys, browser records, database rows, or memory-dump contents. Avoid recursive searches through secrets and private documents.

## Audit sequence

### 1. Establish a baseline

Identify the operating system, local volumes, free space, and requested roots. Record the measurement time and units. Use a shallow disk-usage scan, then drill into the largest relevant children. Include hidden directories and ignored build output where appropriate; a Git-tracked file list is not a disk inventory.

Avoid rescanning the whole machine for each category. Bound expensive scans and report permission errors. Do not follow symlinks or cross into network volumes, mounted disk images, or cloud placeholders without a reason. Directory listings can reveal cloud-only data; do not read it and trigger downloads.

Distinguish allocated disk space from logical file size. APFS clones, hard links, sparse virtual disks, snapshots, and container layers can make directory totals differ from recoverable space. Never add parent folders to their children or sum overlapping measurements. Trash is still occupied space.

### 2. Investigate the owners and causes

Read the relevant reference for each area found:

- [Developer storage](references/developer-storage.md): package stores, build caches, SDKs, test history, and runtime versions.
- [Containers and registries](references/containers.md): local images, build cache, registry layers, and virtual disks.
- [Applications and system data](references/system-storage.md): optional downloads, leftovers, installers, diagnostics, login items, and personal data.

For each material candidate, establish:

1. Exact path or resource, owner, measured size, and whether the size overlaps another finding.
2. What created it and what still references it.
3. Evidence of current use, non-use, or uncertainty.
4. Whether it is reproducible, downloadable, a unique user asset, or unknown.
5. A narrow cleanup option, expected recovery, and the cost of recreation or loss.
6. A prevention option that matches the actual producer of the data.

Use multiple signals for usage: current references, lockfiles, project configuration, installed apps, running processes, service registration, and relevant timestamps. State that installed, enabled at login, and running now are different states. Missing direct imports, an absent process, or an old last-open date alone does not establish non-use.

### 3. Recommend prevention

Prefer supported cleanup features over new scheduled scripts. Check the installed version's help or schema; consult current official documentation when recommending version-dependent settings. Do not copy a setting from a newer release into an older installation.

Separate one-time recovery from recurring growth. Explain whether a proposed setting is a retention rule, a cleanup target, or a hard limit. Keep useful caches when they save real work. Recommend disabling a cache only when its output is not reused or its cost exceeds its benefit.

If a custom policy is justified, specify its scope, selection rule, protected resources, preview mode, locking, stopped-service behavior, and verification. Do not install it during this audit. Do not prescribe one universal age, version count, or size target.

### 4. Return the audit and stop

Lead with the largest supported opportunities and the main sources of repeated growth. Provide:

| Candidate | Evidence and cause | Measured size | Estimated recoverable space | Proposed action | Impact and confidence |
|---|---|---:|---:|---|---|

Use actual inspected paths in the private report. Group findings as:

- **Reproducible cleanup candidates:** generated output or downloads with a clear owner and recovery path.
- **Needs a decision:** personal assets, backups, rollback versions, optional content, or uncertain usage.
- **Keep:** required dependencies, active data, or shared resources with current consumers.
- **Prevention:** producer-specific retention or configuration improvements.
- **Not checked:** denied paths, stopped services, unavailable tools, and unresolved dependencies.

Separate measurements from estimates. Give a combined recovery estimate only for non-overlapping candidates with compatible measurements; otherwise report per-item figures. Explain disk-sharing uncertainty and do not claim space was reclaimed. State explicitly that the audit made no cleanup changes. End with a concrete proposed batch the user can approve, including exact scope and consequences.
