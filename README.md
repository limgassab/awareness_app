# Inner Path · Chemin intérieur

**Inner Path / Chemin intérieur** is a bilingual, installable personal-growth app. It helps a person choose an intention in the morning, record meaningful moments during the day, and reflect briefly in the evening.

The app is intentionally simple. It is not a long questionnaire, a social network, or a clinical assessment. Users can write freely and keep a private record of what they are working on and experiencing.

## Main experience

### 1. Morning intention

The app asks one central question:

> What would you like to work on today?  
> Sur quoi aimeriez-vous travailler aujourd’hui ?

The user can write anything. Optional themes are provided only as inspiration:

- Thankfulness / Gratitude
- Humility / Humilité
- Helping others / Aider les autres
- Kindness / Bienveillance
- Patience / Patience
- Courage / Courage
- Calm / Calme
- Focus / Concentration
- Listening / Écoute
- Self-discipline / Discipline personnelle
- Forgiveness / Pardon
- A personal intention / Une intention personnelle

A small action for the day can be added, but it is optional.

### 2. Record a moment

During the day, the user can press **Record a moment / Noter un moment** and write freely. A moment can be positive, difficult, ordinary, meaningful, or simply something the person wants to remember.

The main entry screen asks only what happened. The user may also add:

- one photo;
- one audio recording;
- an optional category;
- an optional feeling.

Categories and feelings are placed inside an optional section so that recording a moment remains quick.

### 3. Optional pause for a difficult moment

A pause is offered only when the user marks an entry as a **difficult moment**. It is never forced.

Available neutral actions include:

- breathe slowly;
- take a short walk;
- pause quietly;
- write what is needed;
- reflect;
- talk to someone;
- choose a personal action.

After the pause, the app asks only whether the person feels:

- better;
- about the same;
- more difficult.

An additional note is optional.

### 4. Evening reflection

The evening reflection shows the morning intention and asks:

1. How did it go today?
2. What would you like to remember from today? — optional
3. Would you like to continue with the same intention tomorrow? — optional

## App sections

The bottom navigation has four clear sections:

- **Today / Aujourd’hui**: morning intention, the Record a moment button, evening reflection, and recent moments.
- **Record / Noter**: create a new moment using text, photo, or audio.
- **Journey / Parcours**: review intentions, moments, reflections, and recurring themes.
- **Settings / Réglages**: language, appearance, prompt times, backup, restore, privacy, and deletion.

A complete list of moments can also be opened from the Today page.

## Languages

The interface is fully available in:

- English
- Français

The language can be changed from the top of the app or in Settings. A user’s own writing is never translated or modified.

## Appearance

The app uses a calm, nature-inspired visual system:

- forest green for the main identity;
- warm cream for morning intention;
- sage for moments;
- muted coral for difficult moments;
- soft blue-lavender for evening reflection.

Appearance options:

- follow the device setting;
- light mode;
- dark mode.

## Technology used

This is a static Progressive Web App built without a JavaScript framework or backend.

### Frontend

- HTML5
- CSS3
- Vanilla JavaScript
- Responsive mobile-first layout
- Hash-based single-page navigation
- Web Media APIs for microphone recording
- File input and camera/gallery access for photos

### Progressive Web App

- `manifest.webmanifest` provides the install name, colours, scope, and icons.
- `sw.js` provides offline caching and app updates.
- `icon-192.png` and `icon-512.png` are the app icons.
- The app can be installed or added to a phone’s home screen.

### Storage

The app follows a local-first model:

- `localStorage` stores intentions, written moments, reflections, preferences, and attachment references.
- `IndexedDB` stores photo and audio files as binary blobs.

There is no account and no cloud database in this version.

### Hosting

The project is designed for GitHub Pages. It can also be hosted on any HTTPS static web host.

## Repository structure

```text
/
├── index.html
├── manifest.webmanifest
├── sw.js
├── icon-192.png
├── icon-512.png
└── README.md
```

## Deploying with GitHub Pages

1. Upload all files to the root of a GitHub repository.
2. Commit the files to the deployment branch, normally `main`.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select `main` and `/ (root)`.
6. Save the Pages setting.
7. Wait for deployment, then open the GitHub Pages URL.

After the first setup, future commits deploy automatically. The Pages Save button does not need to be pressed again unless the deployment source changes.

## Installing on a phone

### iPhone or iPad

1. Open the live app URL in Safari.
2. Tap Share.
3. Choose **Add to Home Screen**.
4. Confirm the app name.

### Android

1. Open the live app URL in Chrome.
2. Open the browser menu.
3. Choose **Install app** or **Add to Home screen**.

## Updating the app

The service worker currently uses:

```js
const CACHE_NAME = 'inner-path-cache-v2';
```

For a later major release, change it to a new value such as `inner-path-cache-v3`, then commit the updated files.

## Data migration

The app keeps the existing storage key and IndexedDB database used by the previous generated Inner Path version. It also checks the earlier Stress Loop storage keys.

When earlier Stress Loop data is found:

- previous notes become recorded moments;
- previous stress events become difficult moments;
- previous short actions and outcomes are preserved;
- previous daily reviews become earlier reflections.

Keeping the same GitHub Pages URL is important because browser data is connected to the exact website address.

## Backup and restore

Settings includes JSON backup and restore.

The JSON backup includes written records, metadata, intentions, reflections, and settings. The binary photo and audio files remain in IndexedDB on the original device and are not currently included in the JSON backup.

## Privacy model

In this version:

- entries stay on the user’s device;
- there is no account;
- there is no cloud database;
- there is no advertising tracker;
- the app does not upload entries, photos, or recordings to a server.

Clearing browser data, deleting site data, or uninstalling the app may remove local records. Users should download backups regularly.

## Important product notes

Before commercial sale or broad public release, the project should receive:

- cross-device browser testing;
- accessibility testing;
- a complete attachment backup format;
- a privacy policy and terms of use;
- a legal review of the final product name;
- a security review if account sync, encryption, payments, or cloud storage are later added.

## Version

Current app version: **1.1.0**
