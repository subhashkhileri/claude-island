# Claude Island

A macOS menu bar app that brings Dynamic Island-style notifications to Claude Code CLI sessions.

## Build Commands

```bash
# Build Release
DEVELOPER_DIR=/Applications/Xcode.app/Contents/Developer /Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuild -project ClaudeIsland.xcodeproj -scheme ClaudeIsland -configuration Release build

# Build output location
/Users/skhileri/Library/Developer/Xcode/DerivedData/ClaudeIsland-etyrsetoebiegtfayvtosxftghhn/Build/Products/Release/Claude Island.app

# Kill running app
pkill -9 "Claude Island"

# Launch app
open "/Users/skhileri/Library/Developer/Xcode/DerivedData/ClaudeIsland-etyrsetoebiegtfayvtosxftghhn/Build/Products/Release/Claude Island.app"
```

## Project Structure

```
ClaudeIsland/
├── App/                    # App lifecycle (AppDelegate, ScreenObserver, WindowManager)
├── Assets.xcassets/        # App icons and images
├── Core/                   # Core logic (NotchViewModel, Debouncer, etc.)
├── Events/                 # Event types and handling
├── Models/                 # Data models (SessionState, SessionPhase, ChatMessage)
├── Resources/              # Sounds and other resources
├── Services/
│   ├── Chat/              # Chat-related services
│   ├── Hooks/             # Claude CLI hooks integration
│   ├── Session/           # Session monitoring and parsing (ClaudeSessionMonitor, ConversationParser)
│   ├── State/             # State management (SessionStore, ToolEventProcessor)
│   ├── Tmux/              # Tmux integration
│   ├── Window/            # Window management (WindowFinder, TerminalFocuser, YabaiController)
│   └── Shared/            # Shared utilities
├── UI/
│   ├── Components/        # Reusable UI components
│   ├── Views/             # Main views (NotchView, ChatView, ClaudeInstancesView)
│   └── Window/            # Window controllers (NotchWindow, NotchWindowController)
└── Utilities/             # Helper utilities
```

## Key Files

- `ClaudeSessionMonitor.swift` - Monitors active Claude Code sessions via hooks
- `ConversationParser.swift` - Parses JSONL conversation files, extracts token usage
- `SessionStore.swift` - Central state store for all session data
- `NotchView.swift` - Main notch UI with session list and animations
- `ChatView.swift` - Full conversation chat view with markdown rendering
- `TerminalFocuser.swift` - Focuses terminal app running Claude session (works with any terminal)

## How It Works

1. Hooks are installed in `~/.claude/hooks/` on first launch
2. Hooks communicate session state via Unix socket to the app
3. App monitors sessions and displays them in notch overlay
4. Permission requests show approve/deny buttons directly in the notch

## Upstream Repository

- Origin: https://github.com/subhashkhileri/claude-island.git
- Upstream: https://github.com/farouqaldori/claude-island

## Requirements

- macOS 15.6+
- Xcode (for building)
- Claude Code CLI

## See Also

- [CHANGELOG.md](CHANGELOG.md) - Version history and merged PRs
