# Developer storage

## Where to look

Discover project roots from the requested workspace and common development directories. Inspect hidden output as well as visible files. Use manifests, lockfiles, workspace files, build configuration, and scripts to identify producers without running scripts.

Common locations include `node_modules`, local and shared package stores, `.next`, custom framework output directories, `dist`, `build`, `.cache`, `.venv`, language caches, compiler output, test results, coverage, benchmark directories, and temporary reports. Inspect tool configuration for additional output paths; do not assume one default build folder contains everything.

## Temporary work and research directories

Within the requested roots, find directories named or configured as `tmp`, `temp`, `.tmp`, `scratch`, `research`, `experiments`, `benchmarks`, `artifacts`, and `context/tmp`. Include ignored and hidden paths. Use bounded, case-insensitive directory discovery rather than searching every file's contents. Names are discovery hints, not evidence that contents are disposable.

Measure large children and inspect file types, dates, run identifiers, and producer references. Look for repeated research downloads, crawl results, exported datasets, screenshots, browser traces, generated previews, benchmark output, abandoned experiment environments, and copied repositories with their own dependencies. Check scripts and configuration for custom output locations.

Separate reproducible intermediate output from source datasets, notebooks, research notes, final reports, citations, and unique experiment results. Check references from code, notebooks, and reports before proposing removal. An untracked file can be the only copy of useful work; an ignored folder can contain active data. Do not classify a research directory as cache based on its name or age.

For apparent duplicates, distinguish exact copies from revisions. Compare bounded metadata or hashes only when useful, and do not read cloud-only files. Check for active writers or open files before recommending a temporary run directory for cleanup. If ownership or reuse is unclear, put it in the decision-needed group.

Report the disposable subset, not the full parent folder. Suggest producer-specific retention for dated runs, a documented location for final research outputs, or cleanup of intermediate files after a completed job. Preserve the inputs and instructions needed to reproduce results. Do not create these policies during the audit.

## Package installations and stores

Separate the active installation, downloaded file content, cached package trees, old versions, tool caches, and shared stores. Measure nested directories without adding them twice. Moving a store elsewhere can shrink a project folder without saving disk space.

Check every consumer before calling a package obsolete:

- Include nested apps, workers, scraper projects, and workspace lockfiles.
- Distinguish direct dependencies from dependencies required by another package.
- Inspect source, scripts, CSS imports, generated code, framework configuration, and implicit type packages.
- Follow references from retained packages. An older version can still be required.
- For content-addressed stores, a file hash may be shared by many packages. Do not estimate recoverable content from version age alone.
- Account for symlinks, hard links, and filesystem clones. A filesystem size is not a guarantee of physical recovery.

Do not recommend deleting all dependencies, removing a package manager, or pruning a shared store merely because the project is large. Compare likely savings: several unused declarations can save almost nothing, while an unused umbrella SDK can bring hundreds of packages.

For an oversized SDK, identify which features import it and whether those features are actually configured or used. Recommend a narrower package when the feature is needed. Recommend removing obsolete integration code only when usage evidence supports it. Check backup scripts and fallback paths, not only the main application. If live settings are outside scope, mark runtime usage unverified.

After a dependency upgrade, inspect for old compiler versions, native binaries, image-processing packages, and removed SDK copies. Estimate cleanup against current locks and retained references. Do not assume uninstalling a dependency also removes its cached copies.

## Framework and compiler output

Break large output into persistent development cache, production cache, compiled code, source maps, benchmark output, and old indexes. Inspect custom output-directory variables and scripts for parallel build trees.

For a Next.js project, inspect the installed version, configuration, `.next` subdirectories, and custom distribution directories. Distinguish webpack cache from Turbopack cache. Check supported garbage collection settings for that exact version. Do not infer the contents or cause of a cache that has already been removed.

A proposed cache clear should identify the narrow directory, active-process checks needed before cleanup, and the slower first rebuild. Prefer built-in removal of obsolete entries when supported. For fresh release directories or ephemeral builders, determine whether persistent production cache is reused before recommending it.

Do not claim a dependency caused a specific number of cache bytes without attribution evidence. Package removal, generated output removal, and shared-store recovery can overlap.

## Test history and release artifacts

Inspect large build folders by artifact type. Separate installers, archives, symbols, derived data, logs, coverage, and test-result bundles such as `.xcresult`. Multiple installers can serve different processor architectures rather than being duplicates.

Recommend retention at the script that creates results. Define how completed success, failure, incomplete runs, and unmarked legacy runs are identified. Sort by reliable run metadata. Do not let a broad directory glob delete unrelated releases or follow symlinks.

A small number of recent successful runs may be enough. Failures can need longer retention, but unlimited failure retention still grows. Propose a separate age or storage review for failures, preserving active investigations. Make the tradeoff explicit instead of silently deleting evidence.

## SDKs and language runtimes

Check project version files and manifests before recommending removal of Ruby, Java, Python, Node, or other runtimes. Multiple versions may support different projects. A system launcher or stub is not proof of an installed runtime.

On macOS, inspect Xcode device-support versions, simulator runtimes, archives, and DerivedData separately. Device support can be downloaded again; archives and symbols may be needed for distributed releases. Mounted simulator images can appear in more than one measurement.

Android state directories can contain debugging keys without an installed SDK. Keys are credentials, not caches. Report only metadata and explain that removal can require devices to authorize the computer again.

Keep application storage, database files, and required generated clients separate from disposable build output.
