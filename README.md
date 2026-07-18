# halcyon_packages_apps_Settings

HalcyonOS fork of [`LineageOS/android_packages_apps_Settings`](https://github.com/LineageOS/android_packages_apps_Settings).

HalcyonOS turns an Android phone into a PSP/PS3-style handheld console: the
[Halcyon Launcher](https://github.com/MrOz59/halcyon-launcher) replaces the home
experience with an XMB. This fork carries the small Settings changes needed so
the stock Android UI never leaks through the console experience.

## What diverges from upstream

The diff is intentionally tiny — Settings itself is untouched except:

- **Boot home (`FallbackHome`).** Between the end of boot and user-unlock, Android
  shows a temporary home with *"Phone is starting…"*, a spinner, and the Android
  status/navigation bars. HalcyonOS replaces it with a plain **black screen + the
  HalcyonOS wordmark** and hides the system bars, so the sequence reads as one
  continuous boot into the XMB. (`res/layout/fallback_home_finishing_boot.xml`,
  `res/values/themes.xml` → `FallbackHome` style, `src/.../FallbackHome.java`.)
  The wordmark is a placeholder text logo — swap for a drawable when a real logo
  asset exists.
- **External-source authorization.** The `MANAGE_UNKNOWN_APP_SOURCES` intent-filter
  is removed so "install unknown apps" authorization stays inside the launcher UI
  rather than dropping the user into Settings. (`AndroidManifest.xml`.)

## Tracking upstream

`main` currently tracks `lineage-23.2`. Rebase onto the matching upstream branch
when syncing; the diff is deliberately minimal to keep merges trivial.

---

Upstream licensing is unchanged; this README only documents the HalcyonOS divergence.
