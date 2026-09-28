# AgentEventBridges

ScriptingBridge protocol definitions for 50+ macOS applications. Use Swift to automate Finder, Safari, Music, Mail, Messages, Xcode, and more — no AppleScript required.

## Supported Apps

Calendar, Contacts, Finder, Mail, Messages, Music, Notes, Numbers, Pages, Photos, Reminders, Safari, Terminal, TextEdit, Xcode, Preview, Keynote, Shortcuts, System Events, System Settings, Script Editor, QuickTime Player, Screen Sharing, TV, VoiceOver, Image Events, Database Events, Adobe Illustrator, Automator, Final Cut Pro, Logic Pro, Google Chrome, Firefox, Microsoft Edge, Pixelmator Pro, Simulator, UTM, and more.

## Installation

```swift
dependencies: [
    .package(url: "https://github.com/AgentiLoop/AgentEventBridges.git", from: "1.1.8"),
]
```

```swift
// One product per app bridge — pull in only what you use:
.target(name: "YourApp", dependencies: [
    .product(name: "MusicBridge", package: "AgentEventBridges"),
    .product(name: "FinderBridge", package: "AgentEventBridges"),
]),
```

## Usage

```swift
import MusicBridge   // re-exports ScriptingBridge, AppKit and Foundation

// Control Music
if let music: MusicApplication = SBApplication(bundleIdentifier: "com.apple.Music") {
    music.playpause?()
    print(music.currentTrack?.name ?? "Nothing playing")
}

// Automate Finder
if let finder: FinderApplication = SBApplication(bundleIdentifier: "com.apple.finder") {
    let desktop = finder.desktop
    print("Desktop items: \(desktop?.files?().count ?? 0)")
}

// Safari JavaScript
if let safari: SafariApplication = SBApplication(bundleIdentifier: "com.apple.Safari") {
    safari.doJavaScript?("document.title", in: safari.windows?().first?.currentTab)
}
```

## Requirements

- macOS 14+ / Swift 6.4
- Apps must have AppleScript/Automation support enabled

## Part of AgentiLoop Agent!

AgentEventBridges is one of the open-source building blocks of **[AgentiLoop Agent!](https://github.com/AgentiLoop/Agent)**, the native AI agent for macOS 14.6+ on Apple Silicon and Intel. Agent! codes in Xcode, drives any Mac app, runs shell as you or as root, and works with 23 LLM providers plus on-device Apple Intelligence.

🌐 [agentiloop.ai](https://agentiloop.ai/) · ⬇️ [Download Agent!](https://github.com/AgentiLoop/Agent/releases/latest) · 🍺 `brew install --cask agentiloop-agent` · 💻 CLIs: [Rust](https://github.com/AgentiLoop/AgentiLoopCLI) / [Go](https://github.com/AgentiLoop/AgentiLoopGo)

**More Agent! packages:** [AgentAccess](https://github.com/AgentiLoop/AgentAccess) · [AgentAudit](https://github.com/AgentiLoop/AgentAudit) · [AgentColorSyntax](https://github.com/AgentiLoop/AgentColorSyntax) · [AgentD1F](https://github.com/AgentiLoop/AgentD1F) · [AgentLLM](https://github.com/AgentiLoop/AgentLLM) · [AgentMCP](https://github.com/AgentiLoop/AgentMCP) · [AgentSwift](https://github.com/AgentiLoop/AgentSwift) · [AgentTerminalNeo](https://github.com/AgentiLoop/AgentTerminalNeo) · [AgentTools](https://github.com/AgentiLoop/AgentTools) · [AgentScripts](https://github.com/AgentiLoop/AgentScripts)

## License

MIT

---

Copyright © 2026 AgentiLoop.ai, a Logos InkPen LLC company. All rights reserved.
