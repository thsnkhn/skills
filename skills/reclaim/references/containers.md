# Containers and registries

## Establish the local scope

Inspect the selected Docker context and endpoint before queries. Report a remote context as out of scope unless explicitly requested. If the local runtime is stopped, inspect available local metadata and report the limitation; do not start it during the audit.

For a running local daemon, useful read-only inspections include `docker system df -v`, image and container listings, volume inspection, `docker buildx ls`, and inspection of existing builders without bootstrapping them. Check command support in the installed version. Do not dump environment variables or registry credentials.

Separate:

1. Local tagged and untagged images.
2. Build cache, including separate builders.
3. Writable container data.
4. Named and anonymous volumes.
5. Registry storage inside a volume.
6. Host virtual-disk allocation.

Shared image layers make totals overlap. A sparse virtual disk's logical capacity differs from allocated host space. Releasing data inside the VM may not immediately release the same host space. Do not recommend deleting the virtual disk to solve an unexplained total.

## Local deployment images

Group images by repository and unique image identity. Multiple tags, including `latest`, can point to one image. Use creation metadata rather than alphabetic tag order to identify recent versions; explain ambiguous ordering.

Identify references from running and stopped containers. Local references do not establish which image runs on remote production servers. Ask for rollback requirements or report that gap before proposing older deployment versions as disposable.

For recurring retention, suggest a configurable number of recent versions per app and preserve required versions. A custom script may be necessary because standard age-based pruning does not express every per-app rule. Its proposed design should include a fixed local endpoint, a dry run, no forced deletion, locking, reliable timestamp handling, and a safe skip when the runtime is unavailable. Define how untagged images and multi-platform identities are handled.

Do not recommend broad system pruning with volume deletion as routine cleanup. A stopped container or apparently unused volume can hold the only database copy.

## Build cache

Identify the builder driver and the effective garbage-collection policy. Native cleanup may use age, storage pressure, reserved space, or maximum usage. Verify the exact meanings for the installed engine and driver before proposing settings.

Prefer built-in cleanup over a cron job. Recommend a target that balances disk use and rebuild time. A reserved-space value or periodic cleanup target is not necessarily a hard limit. Include inactive builders in coverage; one builder's policy may not cover another.

Configuration files can be overridden or ignored. Recommend checking live builder settings after any later authorized change, and disclose restart requirements. Do not restart the engine during the audit.

## Registry versions and layers

A registry holds separate copies of deployment data. Removing local images does not clean it. Identify the registry implementation, storage backend, repositories, tags, manifests, and configuration before recommending cleanup.

For a reachable local registry, use read-only catalog, tag, and manifest requests. Account for pagination and multi-platform manifest indexes. Distinguish tag count from distinct version count. Inspect image configuration timestamps where needed; `latest` is an alias, not a trustworthy chronological record.

A registry cleanup proposal must separate two steps:

1. Remove only selected old manifest references through supported APIs.
2. Reclaim unreferenced content with the registry's supported garbage collector.

Old untagged child manifests can retain layers after tags are removed. Cleanup that includes untagged manifests can also destroy required children if dependencies are not preserved. For a later cleanup, require a preview and recursive verification of retained indexes, child manifests, configurations, and layers across all affected repositories.

Document the registry's supported offline or read-only maintenance procedure so writes do not race with garbage collection. Do not perform deletion or garbage collection as part of the audit. Never edit internal blob directories as a shortcut.

For prevention, prefer the registry's own retention feature when available. Otherwise propose version selection plus a controlled maintenance window for garbage collection. Local image retention and build-cache policies do not cover registry storage. State explicitly whether each separate policy exists or is merely recommended.
