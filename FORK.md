# Riff — Profile & Listening Insights Fork

**Unofficial fork of [Riff](https://github.com/rootscripts/riff) by [Sqwer2017](https://github.com/Sqwer2017).**

This is a personal experiment: I wanted to explore what a local-first profile and listening-insights layer could feel like inside Riff, while keeping the player fast on weaker hardware. It is not an official Riff build and is not affiliated with the Riff team.

## What this fork adds

### Profile hub
- A profile entry in the sidebar with an avatar.
- Editable nickname, handle, bio, avatar, and hero banner.
- Theme-aware glass styling that follows Riff's Material 3 palette, blur, opacity, and font settings.
- Local-first storage: no account, backend, cloud, or telemetry.

### Progression
- 8 ranks with XP thresholds.
- 20 achievements across listening, favorites, playlists, nights, streaks, and profile completion.
- 3 rotating daily quests.
- XP for listening time, new favorites, playlists, and completed quests.
- Track-completion detection based on near-end progress, the `ended` event, and crossfade/track changes, without double counting.

### Listening insights
- A "Listening statistics" modal with 7-day, 30-day, yearly, and all-time ranges.
- A contribution-style heatmap where every square represents a day, with four intensity levels, hover details, and a marker for today.
- Smooth SVG line charts for listening time, completed tracks, and new likes.
- Weekly activity chart and active-day counts.
- Current and best streak: when the current streak is lower, the best streak is shown just to the left.
- Live percentage changes instead of static "NEW" badges.

### Optimized live background
- One global ambient layer behind the whole application.
- Canvas-based embers and bokeh instead of hundreds of individual DOM particles.
- Pre-rendered sprites, adaptive particle count, and capped FPS.
- Large aurora/orb/beam shapes use soft gradients and slow ambient updates rather than continuously animated 60 fps blur.
- Pauses while the window is unfocused or minimized.
- Low-power mode with fewer particles, lower FPS, and no heavy live blur on large panels.
- Respects `prefers-reduced-motion`.

### Window and UI polish
- The top bar acts as an invisible drag zone when the titlebar is hidden.
- Compact window controls for minimize, maximize, and close.
- Double-click on the empty top bar minimizes the window.
- The platform switch sits next to search.
- Playlists moved to the main navigation; My files joined Presets in the secondary action section with matching styling.
- Slightly larger sidebar avatar.

## Performance

Measured in an isolated Electron test on Windows:

- Before the background rework: ~25% total CPU across Electron processes.
- After: ~6–7% CPU in the same scenario.

The measurements depend on hardware, display refresh rate, and the active visualizers. macOS, Linux, and low-end hardware still need independent testing.

## Status

- Based on Riff 44.2.0 / upstream `main` at `33fa5ff`.
- Tested on Windows.
- No new runtime dependencies.
- Local-first: the profile, listening history, achievements, and quests are stored on the local machine.
- This is a fork experiment, not a pull request. The original Riff project and its contributors retain all rights to the upstream code.

## Feedback

The proposal and additional context are in [Issue #236](https://github.com/rootscripts/riff/issues/236).

## Credits

- **Riff**: [rootscripts/riff](https://github.com/rootscripts/riff), MIT License.
- **Profile design and artwork**: profile layout/design inspiration and rank/achievement artwork adapted from the Noctra project.
- **Fork implementation**: [Sqwer2017](https://github.com/Sqwer2017).

## License

This fork keeps the upstream MIT License. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
