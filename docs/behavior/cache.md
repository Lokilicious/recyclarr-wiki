---
id: cache
title: Cache
---

## Summary

The synchronization cache in Recyclarr allows it to more accurately detect changes to custom formats
in the TRaSH guides. This mainly helps cover changes done on the \*arr side, like renames.

Once Recyclarr creates or updates a custom format in \*arr, it records information about it in a
cache file located in the `cache` subdirectory under the main app data location. The [location
varies][app-data] depending on platform.

:::info

The cache files are not meant to be edited by users. In general I recommend leaving them alone.
Recyclarr will manage it for you.

:::

## Relocating Server Instances {#relocating}

Sometimes users relocate an instance of Radarr or Sonarr. They then update the `base_url`
configuration property to have Recyclarr communicate with that service at its new location.

Recyclarr uniquely identifies an instance by its `base_url` value. If the hostname, port, path,
scheme, or any other part of the URL changes (including adding or removing a trailing slash!),
Recyclarr will no longer use the previous cache data and instead will create a new one. This often
results in confusion because users start to see this warning:

> [WRN] Custom Format with name CRiT (Trash ID: 16622a6911d1ab5d5b8b713d5b0036d4) will be skipped
> because another CF already exists with that name (ID: 246). To fix the conflict, delete or rename
> the CF with the mentioned name

This is because Recyclarr no longer believes it owns that CF, even though it created it before the
`base_url` changed. The way to recover in these situations is to temporarily set
[`replace_existing_custom_formats`][replacecf] to `true`. This will give Recyclarr permission to
replace CFs that it doesn't own (i.e. that aren't recorded in the cache). Once replaced, an entry is
added for it in the cache, which means you can set `replace_existing_custom_formats` back to
`false`.

[app-data]: /file-structure.md#appdata-directory
[replacecf]: /yaml/config-yml-reference.md#cf-replace-existing-custom-formats
