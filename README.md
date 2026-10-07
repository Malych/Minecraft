# Minecraft resource packs

Resource packs for EmberLoch and local play. Zips live in the repo root; only one is served to the live server.

## EmberLoch serve path

1. **`serve-pack`** — one line naming the zip EmberLoch should serve (currently `VanillaTweaks_26.3.zip`).
2. **GitHub Release** — publishing a release (or running the publish workflow) attaches that zip as the release asset and writes **`resource-pack-sha1:`** (40 hex) into the release notes.
3. **Server** — EmberLoch’s `server.properties` uses the release asset download URL for `resource-pack` and that SHA-1 for `resource-pack-sha1`. Clients reconnect to pick up a change.

Other zips in the tree (e.g. Waystones, 3D Redstone) are available to download; they do not get `.sha1` sidecars and are not served unless you point `serve-pack` at them and publish a new release.

## Switching what the server serves

1. Put the new zip in the repo root (PR).
2. Set `serve-pack` to that filename.
3. Publish a release (or run **Publish serve pack** with a new tag).
4. Point EmberLoch at the new release URL + `resource-pack-sha1` from the notes.
