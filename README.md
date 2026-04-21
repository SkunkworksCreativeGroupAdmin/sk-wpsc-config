# Skunkworks WP Super Cache Config

This repository holds the centralized WP Super Cache configuration file applied automatically to all Skunkworks-managed WordPress client sites via the **Skunkworks Cache Manager** mu-plugin.

## How It Works

The `skunkworks-cache-manager.php` mu-plugin (deployed to each client's `/wp-content/mu-plugins/`) fetches this file every 30 minutes via WP-Cron. If the **`version`** field has increased, it applies all settings using the official `wp_cache_setting()` API.

## Updating Settings

1. Edit `wpsc-config.json` with your desired settings
2. **Increment the `version` field** (e.g. `1.0.0` → `1.1.0`)
3. Commit and push

Within 30 minutes, all managed sites will automatically apply the new configuration. Low-traffic sites will also sync on the next admin page load.

## Protected Settings (Never Overwritten)

The mu-plugin explicitly protects these site-specific values and will never overwrite them:

- `cache_page_secret`
- `wp_cache_debug_username`
- `cache_path`
- `file_prefix`
- `sem_id`
- `wpsc_version`

## Diagnostic

On each client site, the WP Super Cache admin page (Settings → WP Super Cache) will show a notice indicating the currently applied config version and last sync time.
