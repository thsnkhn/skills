# Applications and system storage

## Inventory before judgment

On macOS, start with local volume usage, the user's home directory, Applications, Downloads, Desktop, Documents, Movies, hidden tool folders, and selected Library subdirectories. Drill down by measured size. macOS Storage categories are broad; “Documents” is not the same as the Documents folder.

Useful installed inspection tools include `df`, bounded `du` scans, file metadata tools, Homebrew listing and dependency queries, process listings, and login-item/service inspection. Use platform equivalents elsewhere. Do not trigger package updates or installations to collect inventory.

Separate installed applications and command-line tools from shared libraries, SDKs, runtimes, and private environments bundled with an app. A small launcher can own a large hidden installation with Python environments, Node packages, models, and source history.

## Application data

Inspect application support, caches, containers, group containers, downloaded content, and private runtime directories. Identify ownership from bundle identifiers, application metadata, configuration, and directory structure.

Distinguish optional maps, geographic datasets, language packs, models, templates, and offline media from user-created databases and documents. Recommend removing only the optional content through a supported app control where available. State whether it will download again automatically.

An absent app in the main Applications folder is only a clue: also consider user Applications, alternate locations, command-line installations, and shared vendor components. Do not label all same-vendor data abandoned when another installed app uses it.

Browser website storage, application profiles, mail, messages, photos, agent history, and local databases are user state. Do not treat them as ordinary cache. Crash dumps can be large and disposable after an investigation, but may contain private memory data; inspect name, date, and size only.

## Downloads and archives

Group installers, archives, disk images, diagnostic dumps, temporary exports, videos, and backups. An installed app can make its downloaded installer unnecessary, unless the exact version is needed for recovery.

A similarly named extracted folder does not prove an archive is redundant. If relevant and permitted, compare archive listings and extracted file metadata without extracting or overwriting files. Flag incomplete verification. Personal backups and media need a user decision, even when old.

Do not infer duplicate content from names alone. Hash only bounded local candidates where the comparison is useful and will not hydrate cloud-only files.

## Background items

Distinguish registration, enabled-at-login state, and current execution. On macOS, inspect user and system LaunchAgents/LaunchDaemons, login-item metadata, running processes, and service-manager state as available. Report permission gaps.

Inspect startup entry targets for missing executables. A broken entry may be a cleanup candidate but often saves little disk space. Updaters and helper services may belong to active apps. State their purpose and the consequence of disabling them; do not call them malicious or unused based on registration alone.

Check relevant shell startup references, global package launchers, and scheduled jobs for abandoned tooling without printing secrets. After a proposed uninstall, identify orphan service entries and shared dependencies separately. Do not unload or disable anything during the audit.

## Measurement and completion

Record allocated versus apparent size when sparse files or clones matter. Distinguish snapshots, purgeable space, and normal file usage. Do not sum a mounted image's contents with its backing file. Avoid blanket recommendations to remove system snapshots or protected system files.

Moving files to Trash is reversible but does not free their space until Trash is emptied. Removing cloud-synced files may propagate deletion to other devices; recommend a supported local-copy removal option when the aim is local space only.

For later cleanup, propose a narrow batch with exact paths, owners, expected recovery, and preservation checks. Keep administrator-only leftovers visibly pending instead of reporting them as removed. Do not claim a machine-wide recovery total from directory estimates collected at different times.
