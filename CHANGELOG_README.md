# Changelog Management

## How to Update the Changelog

The app's version and changelog are managed through the `changelog.json` file. This makes it easy to update release notes without modifying the main application code.

### File Location
```
/workspaces/RosterRank/changelog.json
```

### File Format
```json
{
  "version": "1.3.0",
  "releases": {
    "1.3.0": {
      "date": "2026-02-01",
      "changes": [
        "Feature description 1",
        "Feature description 2",
        "Bug fix description"
      ]
    }
  }
}
```

## Steps to Add a New Release

1. **Open `changelog.json`**

2. **Update the version number** at the top:
   ```json
   "version": "1.3.0"
   ```

3. **Add a new release entry** to the `releases` object:
   ```json
   "1.3.0": {
     "date": "2026-02-01",
     "changes": [
       "Added player statistics dashboard",
       "Improved CSV export with more details",
       "Fixed bug with duplicate detection"
     ]
   }
   ```

4. **Keep previous releases** in the object for version history

5. **Update the service worker cache version** in `service-worker.js`:
   - Change `CACHE_NAME` from `'rosterrank-v9'` to `'rosterrank-v10'` (increment the number)

6. **Deploy the changes** - users will automatically see the update modal on their next visit

## Example: Complete changelog.json

```json
{
  "version": "1.3.0",
  "releases": {
    "1.3.0": {
      "date": "2026-02-01",
      "changes": [
        "Added player statistics dashboard",
        "New dark mode support",
        "Performance improvements"
      ]
    },
    "1.2.0": {
      "date": "2026-01-30",
      "changes": [
        "Enhanced modal dialogs with beautiful animations",
        "Improved duplicate detection with clear warnings",
        "Better user experience and visual polish"
      ]
    },
    "1.1.0": {
      "date": "2026-01-29",
      "changes": [
        "Added duplicate player number detection",
        "Improved modal design"
      ]
    }
  }
}
```

## Automatic Behavior

- **First Visit**: No modal shown
- **Returning Users**: If the version has changed since their last visit, they'll see the "What's New" modal automatically
- **Manual Access**: Users can click "What's New?" in the footer anytime to see current version info
- **Offline Support**: The changelog is cached for offline viewing
