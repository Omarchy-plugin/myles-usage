# myles.usage

Track active and idle time on your Omarchy bar, with searchable reports, goals, focus insights, and timers.

Track active and idle time, then get **searchable reports** out of it: app reviews, category
goals, editable timelines, focus insights, and JSON backup/restore — plus timers.

## What it does

- **Bar:** today, session, uptime, apps, open, idle, or a running timer.
- **Timers:** custom countdowns, with a stopwatch and pomodoro presets.
- **Reports:** searchable activity history, ranked top apps, and per-category time totals.
- **Goals:** set a daily active-time target and per-app limits.
- **Aliases:** label a bundle of apps as one thing ("work", "play") so reports group sensibly.
- **Editable timeline:** correct misattributed or missing time by hand.
- **Focus insights:** where your attention actually went.
- **Backup/restore:** export and import your whole history as JSON.

Idleness is inferred: after `idleThresholdSeconds` with no input, time stops counting as active.

## Configuration

| Setting | Meaning |
| --- | --- |
| `goalMinutes` | Daily active-time goal (15–1440) |
| `customMinutes` | Custom countdown duration (1–240) |
| `idleThresholdSeconds` | Seconds of no input before time counts as idle (10–600) |
| `barMode` | `today` \| `session` \| `uptime` \| `apps` \| `open` \| `idle` \| `timer` |
| `historyDays` / `historyRange` | Days of history to show and select (1–30) |
| `trackApps`, `topApps` | Focused-app tracking and list length |
| `breakReminders`, `breakReminderMinutes` | Idle-break nudges |

## Data and privacy

All history is local to your machine, in a fixed path that does **not** depend on the plugin
id, so it survives uninstall and reinstall:

```
~/.local/state/omarchy/usage/
├── settings.json   # widget settings
├── stats.json      # activity history
└── timers.json     # saved timers
```

Nothing is uploaded. Backups are plain JSON you write yourself, so store them wherever you
already trust.

## Network calls

None. The only external command used is `omarchy-notification-send`, for break reminders, and
it is local.

## Install

```bash
omarchy plugin add https://github.com/Omarchy-plugin/myles-usage.git --enable --yes
```

That clones, validates, installs to `~/.config/omarchy/plugins/myles.usage/`, and places it on your bar.

## Update

```bash
omarchy plugin update myles.usage --yes
```

Or update every git-managed plugin at once:

```bash
omarchy plugin update --yes
```

## Uninstall

omarchy plugin remove myles.usage --yes

## Installing the whole suite

Every plugin in the suite installs with one command, and updates itself
automatically:

```bash
git clone https://github.com/Omarchy-plugin/myles-omarchy-plugins.git
cd myles-omarchy-plugins && ./install.sh
```

See [myles-omarchy-plugins](../myles-omarchy-plugins) for the update mechanism.

## Credits

- Built for [Omarchy](https://omarchy.org).
- Mylesoft — <https://github.com/Omarchy-plugin> — modifications.

Plugins run unsandboxed inside the long-lived `omarchy-shell` process with your user
permissions. Review the source before enabling anything you did not write.
