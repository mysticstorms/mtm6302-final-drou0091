# Music That Scratches the Itch (My Song Journal)

A calm, organized personal music journal built for music lovers who want to record and reflect on the songs they genuinely connect with—without star ratings, algorithms, or distractions.

**Course:** MTM6302

**Developer:** Sneza M. Drouin

**Repository:** [github.com/mysticstorms/mtm6302-final-drou0091](https://github.com/mysticstorms/mtm6302-final-drou0091)

## Overview

Instead of simply liking or rating tracks on a streaming platform, **My Song Journal** gives users a personal space to log a song's title and artist, choose the single musical element that spoke to them most (such as *Lyrics*, *Vocals*, or *Instrumentals*), and write ongoing personal reflection notes for each track. All entries are saved directly in the browser using `localStorage`, requiring no account or external API.

## Features

### Core Features

* **F1 — Add a Song:** Open the add-song form to enter a song title, artist name, and choose one musical element from a preset dropdown (*Lyrics*, *Vocals*, *Composition*, *Instrumentals*, *Uniqueness*, or *All of the above*). Submitting validates all fields, creates a song card with a matching preset cover image, saves to `localStorage`, and displays a confirmation banner.

* **F2 — Remove a Song:** Delete any song card from the journal with a confirmation prompt to prevent accidental data loss.

* **F3 — Personal Log Entries:** Add ongoing reflection notes directly inside each song card. Blank or whitespace-only entries are rejected, and valid notes are immediately saved to `localStorage`.

* **F4 — Remove Log Entries:** Delete individual reflection notes from a song card with a confirmation prompt.

* **F5 — Clear Journal:** Wipe all songs and notes from the interface and `localStorage` (after confirmation), returning the application to its empty welcome state.

### Planned Optional Enhancements

* **Theme Selector:** Switch between provided color themes to match different listening moods.

* **Edit Song:** Update the title, artist, or selected musical element on an existing song card.

### Out of Scope (By Design)

* Star or numeric rating systems

* Custom user-uploaded album covers

* External music APIs (e.g., Spotify, Apple Music)

* User accounts or cloud syncing

## Design & Accessibility

* **Visual Style:** Dark page background paired with high-contrast, off-white rounded song cards.

* **Responsive Layout:**

  * **Wide Screens (Desktop):** Multi-column grid displaying 3–4 song cards per row.

  * **Narrow Screens (Mobile):** Single-column scrollable layout with scaled-up song titles and compact preset imagery.

* **Keyboard Accessibility:** Full keyboard navigation (`Tab`, `Shift+Tab`, `Enter`, `Space`), semantic HTML with associated `<label>` elements, visible focus indicators, and live status/error announcements.

## Tech Stack & Architecture

* **Frontend:** Semantic HTML5, Responsive CSS3, Vanilla JavaScript (ES6+)

* **Persistence:** Browser `localStorage` (no external backend or API)

* **Storage Key:** `mtm6302-music-journal-songs`

### Data Structure

Each song is stored in a `songs` state array with a unique ID and a nested `logs` array. Preset labels, image paths, and alt text are mapped dynamically from a read-only `ELEMENT_OPTIONS` lookup object rather than duplicated in storage.

```javascript
const songs = [
  {
    id: "song-1732620001",
    title: "Bohemian Rhapsody",
    artist: "Queen",
    element: "composition",
    logs: [
      {
        id: "log-1732620055",
        text: "The transition into the operatic section still gives me goosebumps."
      }
    ]
  }
];
```

### Project Structure

```text
mtm6302-final-drou0091/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── app.js
├── assets/
│   └── images/          # 6 preset musical element images/SVGs
└── docs/
    ├── mtm6302-milestone-1-mcdo0765.pdf
    └── lo-fi wireframe/
```

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/mysticstorms/mtm6302-final-drou0091.git
   ```

2. **Navigate into the project folder:**

   ```bash
   cd mtm6302-final-drou0091
   ```

3. **Run the application:**
   Open `index.html` directly in your browser, or use a local development server (such as the VS Code **Live Server** extension).

## Documentation & Wireframes

* **Client Brief:** [mtm6302-milestone-1-mcdo0765.pdf](https://github.com/mysticstorms/mtm6302-final-drou0091/blob/main/docs/mtm6302-milestone-1-mcdo0765.pdf)

* **Low-Fidelity Wireframes:** [docs/lo-fi wireframe](https://github.com/mysticstorms/mtm6302-final-drou0091/tree/main/docs/lo-fi%20wireframe)

## Testing & Acceptance Checklist

| ID | Test Case | Expected Behavior |
| ----- | ----- | ----- |
| **T1** | Initial Empty State | Displays empty-state prompt when no saved data exists. |
| **T2** | F1: Add Valid Song | Creates card with matching preset image, hides empty state, shows confirmation. |
| **T3** | F1: Invalid / Blank Input | Shows validation error; does not add a card or alter `localStorage`. |
| **T4** | F1: Repeated Additions | Renders multiple distinct cards with their respective preset images. |
| **T5** | F3: Add Multiple Logs | Appends reflection notes to the target song card and updates storage. |
| **T6** | F3: Blank Log Entry | Rejects empty/whitespace-only notes without altering existing logs. |
| **T7** | F4: Remove Log Entry | Cancelling keeps the note; confirming removes it and updates storage. |
| **T8** | F2: Remove Song | Cancelling keeps the card; confirming deletes the song and its notes. |
| **T9** | Persistence Across Refresh | Reloading the browser restores all saved songs, images, and logs. |
| **T10** | F5: Clear Journal | Removes all songs and storage key, displays `"Journal Cleared."`, and stays empty on reload. |
| **T11** | Accessibility & Responsive | Full keyboard navigation with focus rings; adapts cleanly between 375px and 1280px. |

## Acknowledgments

* **AI Assistance:** This `README.md` file was drafted and formatted with the assistance of Google Gemini, based on the developer's Milestone 2 Application Plan and Architecture document.

## Author

**Sneza M. Drouin**

Developed for **MTM6302**
