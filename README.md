# BattleLock

<div align="center">

![BattleLock Logo](https://via.placeholder.com/150x150.png?text=BL)

**Advanced Combat Tagging System for Paper 1.21+**

[![Paper](https://img.shields.io/badge/Paper-1.21+-blue.svg)](https://papermc.io/)
[![Java](https://img.shields.io/badge/Java-17+-orange.svg)](https://adoptium.net/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## 📋 Overview

**BattleLock** is a modern, feature-rich combat tagging plugin for Paper servers that prevents players from escaping combat through various means. With extensive visual effects, per-world configurations, and comprehensive restriction options, BattleLock provides an immersive and fair PvP experience.

## ✨ Features

### Core Functionality
- 🎯 **Advanced Combat Tagging** - Automatic tagging when players engage in PvP
- ⏱️ **Configurable Duration** - Set combat duration per-world
- 🌍 **Per-World Settings** - Different rules for different worlds
- 🛡️ **Permission-Based Bypass** - Allow certain players to bypass restrictions

### Visual Effects
- ✨ **Glowing Effect** - Make combat players visible with colored outlines
- 🎆 **Particle Effects** - Spawn configurable particles around combat players
- 📊 **Boss Bar Timer** - Display combat time remaining with customizable boss bars
- 💬 **Action Bar Messages** - Show combat status in the action bar

### Restrictions
- 🚫 **Block Ender Pearls** - Prevent teleportation escape
- 🪽 **Block Elytra** - Disable flying during combat
- 🍃 **Block Chorus Fruit** - Prevent chorus fruit teleportation
- ⚔️ **Block Commands** - Customizable command blacklist
- 🛏️ **Block Bed Setting** - Prevent respawn point changes
- 🪣 **Block Buckets** - Optional bucket usage restriction
- 🚁 **Disable Flight** - Remove flight ability during combat

### Combat Logging Protection
- 👤 **NPC Spawning** - Spawn an NPC when players log out (requires Citizens)
- 💀 **Kill on Logout** - Optional instant death for combat loggers
- 📢 **Broadcast Messages** - Alert server when someone combat logs
- 🎒 **Item Drops** - Drop inventory and experience on combat log
- ⏲️ **Configurable NPC Duration** - How long the NPC stays

### Additional Features
- 📝 **Comprehensive Commands** - Admin tools for managing combat
- 🔧 **Hot Reload** - Reload configuration without restart
- 🐛 **Debug Mode** - Detailed logging for troubleshooting
- 🎨 **Fully Customizable Messages** - Modify all plugin messages

---

## 📦 Installation

### Requirements
- **Server Software**: Paper 1.21+ (or Folia)
- **Java Version**: Java 17 or higher
- **Optional**: Citizens (for NPC spawning)

### Steps

1. **Download** the latest BattleLock JAR from [Releases](https://github.com/yourusername/battlelock/releases)

2. **Place** the JAR file in your server's `plugins/` folder

3. **Restart** your server

4. **Configure** the plugin by editing `plugins/BattleLock/config.yml`

5. **Reload** the configuration with `/battlelock reload`

---

## 🎮 Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/battlelock` | Main plugin command | `battlelock.admin` |
| `/battlelock reload` | Reload configuration | `battlelock.reload` |
| `/battlelock status [player]` | Check combat status | `battlelock.status` |
| `/battlelock tag <player>` | Manually tag a player | `battlelock.tag` |
| `/battlelock untag <player>` | Remove combat tag | `battlelock.untag` |
| `/battlelock list` | List all players in combat | `battlelock.status` |
| `/combat` | Check your own combat status | None |

**Aliases**: `/bl`, `/combattag`, `/ct`

---

## 🔐 Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `battlelock.admin` | Access to all commands | OP |
| `battlelock.bypass` | Bypass combat restrictions | OP |
| `battlelock.notify` | Receive combat log notifications | OP |
| `battlelock.reload` | Reload configuration | OP |
| `battlelock.status` | Check combat status | OP |
| `battlelock.tag` | Manually tag players | OP |
| `battlelock.untag` | Remove combat tags | OP |

---

## ⚙️ Configuration

### Basic Example

```yaml
# Combat duration in seconds
combat-duration: 15

# Restrictions
restrictions:
  enderpearls: true
  elytra: true
  chorus-fruit: true
  disable-flight: true
  block-teleport: true
  
  blocked-commands:
    - /spawn
    - /home
    - /tpa

# Visual Effects
visual-effects:
  glowing:
    enabled: true
    color: RED
    
  boss-bar:
    enabled: true
    title: "&c⚔ &lCOMBAT MODE &c⚔"
    color: RED
```

### Per-World Configuration

```yaml
worlds:
  world-specific:
    world:
      combat-duration: 15
      restrictions:
        enderpearls: true
        
    world_nether:
      combat-duration: 20
      restrictions:
        enderpearls: false  # Allow pearls in nether
        
    pvp_arena:
      combat-duration: 30
      visual-effects:
        glowing:
          color: YELLOW
```

### Full Configuration

See [config.yml](src/main/resources/config.yml) for all available options.

---

## 🎨 Visual Effects Guide

### Glowing Colors
Available colors: `RED`, `BLUE`, `GREEN`, `YELLOW`, `PURPLE`, `PINK`, `WHITE`

### Particles
Available particle types:
- `FLAME` - Fire particles
- `SMOKE` - Smoke effect
- `SPELL` - Magic sparkles
- `REDSTONE` - Colored dust
- `HEART` - Hearts
- `ANGRY_VILLAGER` - Anger marks
- `ENCHANT` - Enchantment glyphs

### Boss Bar Styles
- `SOLID` - Single solid bar
- `SEGMENTED_6` - Bar with 6 segments
- `SEGMENTED_10` - Bar with 10 segments
- `SEGMENTED_12` - Bar with 12 segments
- `SEGMENTED_20` - Bar with 20 segments

---

## 🔧 Building from Source

### Prerequisites
- JDK 17 or higher
- Maven 3.6+

### Build Steps

```bash
# Clone the repository
git clone https://github.com/yourusername/battlelock.git
cd battlelock

# Build with Maven
mvn clean package

# The compiled JAR will be in target/BattleLock-1.0.0.jar
```

---

## 📖 Usage Examples

### Basic PvP Server Setup

```yaml
combat-duration: 10
restrictions:
  enderpearls: true
  elytra: true
  blocked-commands:
    - /spawn
    - /home
visual-effects:
  glowing:
    enabled: true
  boss-bar:
    enabled: true
```

### Hardcore PvP Setup

```yaml
combat-duration: 30
restrictions:
  enderpearls: true
  elytra: true
  chorus-fruit: true
  disable-flight: true
  block-teleport: true
  block-buckets: true
  blocked-commands:
    - /spawn
    - /home
    - /tpa
    - /warp
combat-logging:
  enabled: true
  kill-on-logout: true
  broadcast: true
```

### Casual Server Setup

```yaml
combat-duration: 5
restrictions:
  enderpearls: false  # Allow pearls
  elytra: false       # Allow elytra
  disable-flight: false
visual-effects:
  action-bar:
    enabled: true
  boss-bar:
    enabled: false
```

---

## 🐛 Troubleshooting

### Combat tags not working
1. Check if the plugin is enabled in the world: `/battlelock status`
2. Verify the player doesn't have bypass permission
3. Enable debug mode and check console logs

### Visual effects not showing
1. Ensure visual effects are enabled in config.yml
2. Check particle type and boss bar settings are valid
3. Verify the player's client supports the effects

### Commands are blocked even when not in combat
1. Check the allowed-commands list in config
2. Verify command isn't in the blocked list twice
3. Reload the config: `/battlelock reload`

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License

---

## 🙏 Acknowledgments

- Paper team for the excellent server software
- Citizens plugin for NPC API reference
- All contributors and users of BattleLock
- darkkarma111 fo helping develop this plugin

---

## 📞 Support

- **Discord**: [Join our Discord](https://discord.gg/GR7H2ZJr2M)

---

<div align="center">

Made with ❤️ for the Minecraft community

⭐ **Star this repository if you find it helpful!** ⭐

</div>
