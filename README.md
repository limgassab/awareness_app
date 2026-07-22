# Daily Reflection · Réflexion quotidienne

**Daily Reflection / Réflexion quotidienne** is a bilingual, installable personal-growth journal. It helps a person choose a simple intention in the morning, record meaningful moments during the day, and reflect briefly in the evening.

The app is intentionally simple. It is not designed as a long questionnaire, a social network, or a clinical assessment. A user can write freely and keep a private record of what they are working on and experiencing.

## Main experience

### Morning intention

The app asks one central question:

> What would you like to work on today?  
> Sur quoi aimeriez-vous travailler aujourd’hui ?

A person can write anything. Optional themes are provided only as inspiration:

- Gratitude / Gratitude
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

The user may also add one optional small action for the day.

### Record a moment

During the day, the user can record:

- a good moment;
- a difficult moment;
- a moment of growth;
- something to remember;
- another freely described moment.

A moment can contain:

- written text;
- an optional feeling;
- one photo;
- one audio recording.

The app is not limited to stress. It can record joy, gratitude, calm, pride, connection, fear, stress, sadness, anger, or another feeling.


### Fact of the day

The Today screen displays one short science fact each calendar day. The same fact remains visible throughout the day and changes automatically on the next day.

The fact library is stored directly in `index.html`, so the text remains available offline. Each fact contains:

- an English version;
- a French version;
- a category;
- the name of the scientific organization;
- a link to the original source.

The current library contains curated facts about the brain, sleep, the human body, genetics, animals, plants, fungi, water, oceans, Earth, and space. Sources include NIH, NINDS, NIBIB, NCBI, NHGRI, NHLBI, NOAA, NASA, USGS, the Smithsonian Institution, and the U.S. National Park Service. The source link requires internet access, but the fact itself works offline.

### Optional short reset

For a difficult moment, the user can optionally start a short reset. Available actions include breathing slowly, taking a short walk, pausing in silence, writing, reflecting, talking to someone, or choosing a personal action.

After the reset, the person can record how the moment changed. This feature is optional and is not the central identity of the app.

### Evening reflection

The evening check-in is deliberately brief. The app displays the morning intention and asks:

1. How did it go today?
2. What would you like to remember from today? — optional
3. Would you like to continue with the same intention tomorrow? — optional

## App sections

- **Today / Aujourd’hui**: greeting, current intention, quick moment entry, optional reset, and evening reflection.
- **Record / Noter**: record a moment using text, photo, or audio.
- **Moments**: private chronological record of meaningful experiences.
- **Journey / Parcours**: gentle summaries of intentions, moments, reflections, and recurring themes.
- **Settings / Réglages**: language, appearance, daily prompt times, backup, restore, privacy, and deletion.

## Languages

The complete interface is available in:

- English
- Français

The language can be changed from the top of the app or in Settings. A user’s own writing is never automatically translated or modified.

## Appearance

The app uses a calm, modern visual system:

- forest green as the main identity;
- muted blue for the science fact card;
- warm cream for morning intention;
- sage for meaningful moments;
- muted coral for difficult moments;
- soft blue-lavender for evening reflection.

Three appearance modes are available:

- follow the device setting;
- light mode;
- dark mode.

The interface is mobile-first and includes a fixed bottom navigation bar. It also works on desktop screens.

## Technology used

This project is a static Progressive Web App built without a JavaScript framework or backend.

### Frontend

- HTML5
- CSS3
- Vanilla JavaScript
- Responsive mobile-first layout
- Hash-based single-page navigation
- Web Media APIs for microphone recording
- File input and camera/gallery access for photos

### Progressive Web App

- `manifest.webmanifest` provides install information, name, colours, and icons.
- `sw.js` is the service worker used for offline caching and app updates.
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
2. Commit the files to the branch used for deployment, normally `main`.
3. Open **Settings → Pages** in the repository.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and the `/ (root)` folder.
6. Save the Pages setting.
7. Wait for the deployment to finish, then open the GitHub Pages URL.

After the first deployment, future commits to the configured branch are deployed automatically. The Pages **Save** button does not need to be pressed again unless the deployment source is changed.

## Installing on a phone

### iPhone or iPad

1. Open the live app URL in Safari.
2. Tap the Share button.
3. Choose **Add to Home Screen**.
4. Confirm the app name.

### Android

1. Open the live app URL in Chrome.
2. Open the browser menu.
3. Choose **Install app** or **Add to Home screen**.

## Updating the app

The service worker uses a named cache:

```js
const CACHE_NAME = 'daily-reflection-cache-v3';
```

For a major published update, change the cache name to a new value, for example:

```js
const CACHE_NAME = 'inner-path-cache-v2';
```

Then commit both the changed application files and `sw.js`. The service worker also uses a network-first strategy for HTML so new versions are normally detected automatically.

## Data migration from the earlier app

The app checks for the earlier storage key used by **Stress Loop Mini App**. When old data is found, it is migrated automatically:

- previous text, photo, and audio notes become moments to remember;
- previous stress events become difficult moments;
- previous short actions and before/after results are preserved;
- previous daily reviews are preserved as earlier reflections.

The IndexedDB database name is intentionally retained so earlier photo and audio attachments remain accessible.

Do not manually change the storage keys or database name unless a tested migration is also added.

## Backup and restore

Settings includes a JSON backup and restore function.

The JSON backup contains:

- intentions;
- moment text and metadata;
- evening reflections;
- settings;
- references to attachments.

Current limitation: the actual binary photo and audio files are not included in the downloaded JSON file. They remain in IndexedDB on the original device. A future release can add a complete archive format containing both records and attachments.

## Privacy model

In this version:

- entries are stored locally on the device;
- there is no account;
- there is no cloud synchronization;
- there is no advertising tracker;
- there is no analytics service;
- photos and audio are not uploaded to a server by the application.

Important limitations:

- someone with access to the unlocked device may be able to open the app;
- clearing site data can erase records;
- uninstalling the app or browser may erase local records;
- records do not automatically synchronize across devices;
- the app is not a substitute for professional medical or mental-health care.

A commercial release should include a reviewed privacy policy, terms of use, clear support contact, and an accurate explanation of data storage for each distribution platform.

## Browser support

The core written journal works in modern browsers. Photo selection works in modern mobile and desktop browsers.

Audio recording requires:

- microphone permission;
- `navigator.mediaDevices.getUserMedia`;
- the browser `MediaRecorder` API.

Audio format is selected according to browser support. Some older versions of Safari may not support recording or may use a different format.

Daily morning and evening prompts are displayed when the app is open after the selected time. A static GitHub Pages PWA cannot guarantee background notifications while the app is fully closed. True push notifications would require additional infrastructure and platform-specific permission handling.

## Suggested release testing

Before publishing a version, test the following in both English and French:

1. Set and edit a morning intention.
2. Enter a free-form intention without relying on a predefined theme.
3. Record each type of moment.
4. Save a text-only moment.
5. Save and reopen a photo moment.
6. Record, stop, save, and replay an audio moment.
7. Start and complete a short reset.
8. Complete the evening reflection.
9. Continue an intention to the next day.
10. Change light, dark, and system appearance.
11. Refresh the page and confirm that entries remain.
12. Install the PWA and reopen it from the home screen.
13. Test offline opening after the first successful online load.
14. Download a backup and restore it in a separate test browser profile.
15. Confirm that old Stress Loop data is migrated in a test profile before updating the public app.

## Commercial-development considerations

The current code is suitable as a local-first prototype or small static product. A larger commercial service may later require:

- encrypted cloud synchronization as an explicit optional feature;
- user authentication;
- complete attachment backup and restore;
- account deletion workflows;
- a support and error-reporting process;
- accessibility testing;
- legal review of privacy and wellbeing claims;
- app-store packaging for native iOS and Android distribution;
- trademark and product-name checks before final branding.

The working product name in this repository is **Daily Reflection / Réflexion quotidienne**. A trademark and marketplace search should be completed before using the name commercially.

## Version

Current application version: **1.0.0**
