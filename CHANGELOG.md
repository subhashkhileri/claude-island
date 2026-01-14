# Changelog

## 2025-01-14 - Merged Upstream PRs

Merged 8 open PRs from upstream repository (https://github.com/farouqaldori/claude-island):

### PR #17 - Fix: Don't trigger alert when context resumes
- **Author:** lekman
- **File:** `NotchView.swift`
- Filters out context resume messages from triggering notifications
- Prevents alerts when session continues from previous conversation

### PR #21 - Fix: Increase menu height so Quit button is interactive
- **Author:** gwtaylor
- **File:** `NotchView.swift`
- Fixes menu clipping issue where Quit button was not clickable

### PR #23 - Fix: Prevent window flicker when waking from sleep
- **Author:** gwtaylor
- **Files:** `ScreenObserver.swift`, `WindowManager.swift`
- Debounces screen change events to prevent UI flicker on wake

### PR #25 - Fix: Enable single-click to open chat rows
- **Author:** saoudrizwan
- **File:** `ClaudeInstancesView.swift`
- Chat rows now respond to single click instead of requiring double-click

### PR #26 - Fix: Prevent collapsed spinner/checkmark from clipping into notch
- **Author:** saoudrizwan
- **Files:** `NotchView.swift`, `NotchWindowController.swift`
- Fixes visual clipping of status indicators in collapsed state

### PR #33 - Add image paste support in chat
- **Author:** ryskin
- **File:** `ChatView.swift`
- Enables pasting images directly into chat input
- Supports drag-and-drop and clipboard paste

### PR #34 - Add status fallback and periodic session recheck
- **Author:** ryskin
- **Files:** `ClaudeSessionMonitor.swift`, `SessionStore.swift`, `ClaudeInstancesView.swift`
- Adds periodic session status recheck for reliability
- Shows phase-based status text as fallback when no message content

### PR #35 - Add terminal focus button that works with any terminal app
- **Author:** ryskin
- **Files:** `TerminalFocuser.swift` (new), `ClaudeInstancesView.swift`
- New TerminalFocuser service that works with any terminal (iTerm2, Warp, Terminal.app, Ghostty, Kitty, Alacritty, WezTerm)
- Replaces yabai-dependent focus with native NSWorkspace approach
- Shows terminal button when session has PID (no longer requires tmux)

### Additional Changes

- **Removed analytics code** - Mixpanel and Sparkle already removed in commit `1b13057`
- **Updated README.md** - Removed outdated analytics section
- **Token usage display** - Shows formatted token count (e.g., "12.5K") in session rows
- **Improved tool input formatting** - Better display of tool parameters in permission prompts

### Files Modified

```
M  ClaudeIsland/App/ScreenObserver.swift           # PR #23 - debounce screen changes
M  ClaudeIsland/App/WindowManager.swift            # PR #23 - debounce screen changes
M  ClaudeIsland/Core/NotchViewModel.swift          # Minor fixes
M  ClaudeIsland/Models/SessionPhase.swift          # PR #35 - improved formattedInput
M  ClaudeIsland/Models/SessionState.swift          # PR #35 - usage property
M  ClaudeIsland/Services/Session/ClaudeSessionMonitor.swift  # PR #34 - periodic recheck
M  ClaudeIsland/Services/Session/ConversationParser.swift    # PR #34/35 - UsageInfo parsing
M  ClaudeIsland/Services/State/SessionStore.swift  # PR #34 - status fallback
M  ClaudeIsland/UI/Views/ChatView.swift            # PR #33 - image paste support
M  ClaudeIsland/UI/Views/ClaudeInstancesView.swift # PR #25/34/35 - single-click, status, terminal focus
M  ClaudeIsland/UI/Views/NotchView.swift           # PR #17/21/26 - alerts, menu, clipping
M  ClaudeIsland/UI/Window/NotchWindowController.swift  # PR #26 - clipping fix
M  README.md                                       # Removed analytics section
A  ClaudeIsland/Services/Window/TerminalFocuser.swift  # PR #35 - new file
```
