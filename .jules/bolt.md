## 2024-05-22 - [Pattern: O(N) Resource Substring Search to O(1) Hash Cache]
**Learning:** Functions in AppStream that validate strings against a registry (categories, TLDs, triplets) were loading text from GResource and using `strstr` for every call. This is O(N) and costly during bulk validation.
**Action:** Use `GHashTable` combined with `g_once_init_enter` to cache split lines from resources. This provides O(1) lookup and avoids repeated string allocations and resource lookups.

## 2024-05-22 - [Environment: Missing pkg-config for GLib]
**Learning:** In some sandbox environments, `pkg-config` might not find GLib even if headers/libs are present in standard locations (e.g. `/usr/include/glib-2.0`). This blocks `meson setup`.
**Action:** Manually check `PKG_CONFIG_PATH` or common include paths. If still failing, rely on thorough manual verification and known-good patterns for code correctness.
