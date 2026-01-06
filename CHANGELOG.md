# Changelog

All notable changes to BattleLock will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2024-01-XX

### Added
- ✨ Initial release of BattleLock
- 🎯 Automatic combat tagging when players engage in PvP
- ⏱️ Configurable combat duration (per-world support)
- ✨ Visual effects system:
  - Glowing effect with customizable colors
  - Particle effects around combat players
  - Boss bar with combat timer
  - Action bar messages
- 🚫 Comprehensive restriction system:
  - Block ender pearls during combat
  - Block elytra usage during combat
  - Block chorus fruit teleportation
  - Block specific commands (customizable list)
  - Disable flight during combat
  - Block world teleportation
  - Block bed spawn setting
  - Block bucket usage
  - Block item dropping/pickup (optional)
- 🛡️ Combat logging protection:
  - Drop inventory on combat log
  - Drop experience on combat log
  - Kill on logout option
  - Broadcast combat log messages
  - NPC spawning support (requires Citizens)
- 🌍 Per-world configuration system
- 🔧 Admin commands:
  - `/battlelock reload` - Reload configuration
  - `/battlelock status` - Check combat status
  - `/battlelock tag` - Manually tag players
  - `/battlelock untag` - Remove combat tags
  - `/battlelock list` - List players in combat
- 👤 Player command:
  - `/combat` - Check personal combat status
- 🎨 Fully customizable messages
- 🔐 Permission-based bypass system
- 🐛 Debug mode for troubleshooting
- 📊 Minimum damage threshold configuration
- 🎯 Support for projectile combat
- ⚙️ Advanced settings for mob combat tagging
- 🔄 Automatic combat expiration checking
- 🎨 Multiple boss bar styles and colors
- 🌈 Multiple particle types supported

### Technical Details
- Built for Paper 1.21+
- Requires Java 17 or higher
- Uses modern Kyori Adventure API for text components
- Efficient async task system for combat checking
- Clean, modular code structure
- Extensive configuration validation
- No external dependencies (except optional Citizens)

### Known Issues
- NPC spawning requires Citizens plugin (placeholder implementation included)
- Glowing color changes require scoreboard team management (basic implementation)

---

## Upcoming Features (Future Releases)

### [1.1.0] - Planned
- 📊 Statistics tracking (kills, deaths, combat logs)
- 💾 Database support (MySQL/SQLite) for persistent data
- 🎮 Integration with popular economy plugins
- 🏆 Combat leaderboards
- 📝 Combat log history
- 🔔 Advanced notification system
- 🌐 PlaceholderAPI support
- 🗺️ Combat region support (WorldGuard integration)

### [1.2.0] - Planned
- 🤖 Standalone NPC implementation (no Citizens required)
- 🎯 Custom hit detection improvements
- 🔊 Sound effects for combat events
- 📱 Discord webhook integration
- 🎨 Custom particle trails
- 🏃 Movement speed modifications during combat
- ⚔️ Combat scoreboard sidebar
- 🎯 Hit accuracy tracking

### [1.3.0] - Planned
- 🌟 Combat rewards system
- 🏅 Ranking system
- 📈 Combat analytics dashboard
- 🔌 API for other plugins
- 🎭 Custom combat modes
- 🎪 Event system for combat
- 🎁 Loot tables for combat logs
- 🌍 Multi-server support (BungeeCord/Velocity)

---

## Version History

### Release Types
- **Major Release** (X.0.0) - Significant new features, possible breaking changes
- **Minor Release** (1.X.0) - New features, backwards compatible
- **Patch Release** (1.0.X) - Bug fixes, minor improvements

### Support Policy
- Latest major version: Full support with updates
- Previous major version: Security updates only
- Older versions: No support, please upgrade

---

## Contributing

Want to suggest a feature or report a bug?
- Create an issue on [GitHub](https://github.com/yourusername/battlelock/issues)
- Join our [Discord](https://discord.gg/yourdiscord) community
- Submit a pull request with your changes

---

## Links

- [GitHub Repository](https://github.com/yourusername/battlelock)
- [Documentation](https://github.com/yourusername/battlelock/wiki)
- [Discord Server](https://discord.gg/yourdiscord)
- [Download Latest Release](https://github.com/yourusername/battlelock/releases/latest)
