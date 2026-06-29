# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2026-06-29

### Added

- `@scroll_revamped_passthrough_alternate` (default `on`) passes the wheel to any
  app on the alternate screen, so full-screen TUIs that are not on the app list,
  such as Claude Code, scroll themselves instead of dropping into copy-mode over
  the primary-screen scrollback behind them. Set it `off` to route purely by the
  app list.

### Fixed

- A full-screen app not on the passthrough list received copy-mode scrolling of
  the scrollback behind it instead of the wheel. The routing now also keys on
  `#{alternate_on}`.

## [1.1.0] - 2026-06-23

### Added

- `@scroll_revamped_speed` throttles copy-mode wheel scrolling to a fixed number
  of lines per tick, so a fast trackpad flick no longer jumps whole pages
  (upstream tmux-mighty-scroll #7).

## [1.0.0] - 2026-06-22

### Added

- Smart mouse wheel: full-screen apps (vim, less, htop) receive the wheel
  directly, everything else enters copy-mode.
- On tmux 3.1+ the routing is a native regex match over the pane's foreground
  command, with no process-tree walk and no fork per wheel event.
- A graceful per-event check fallback for older tmux.
- Configurable passthrough app list and an opt-out for mouse management.
