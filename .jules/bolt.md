## 2025-01-24 - [GHashTable Caching for Resource Lists]
**Learning:** Functions that perform repeated resource lookups and linear string searches on large text data are a common performance bottleneck. Caching these into a `GHashTable` with lazy initialization via `g_once_init_enter` provides a significant O(1) speedup.
**Action:** Always look for `g_resource_lookup_data` followed by `g_strstr_len` or linear searches in loops as candidates for `GHashTable` caching.
