# BattleLock Quick Start Guide

Get BattleLock up and running in 5 minutes!

## 🚀 Installation

1. **Download** BattleLock-1.0.0.jar
2. **Place** in your server's `plugins/` folder
3. **Restart** your server
4. **Done!** BattleLock is now active with default settings

## ⚡ Basic Usage

### For Players

Check if you're in combat:
```
/combat
```

### For Admins

Check combat status:
```
/bl status [player]
```

Manually tag a player:
```
/bl tag <player>
```

Remove combat tag:
```
/bl untag <player>
```

List all players in combat:
```
/bl list
```

Reload configuration:
```
/bl reload
```

## 🎯 Default Settings

- **Combat Duration**: 15 seconds
- **Ender Pearls**: ❌ Blocked
- **Elytra**: ❌ Blocked  
- **Flight**: ❌ Blocked
- **Glowing Effect**: ✅ Enabled (Red)
- **Boss Bar**: ✅ Enabled
- **Combat Logging**: ✅ Enabled

## 🔧 First-Time Configuration

### Step 1: Choose Your Server Style

**Casual PvP Server?**
Edit `plugins/BattleLock/config.yml`:
```yaml
combat-duration: 5  # Shorter combat time
restrictions:
  enderpearls: false  # Allow pearls
  elytra: false       # Allow elytra
```

**Hardcore PvP Server?**
```yaml
combat-duration: 30  # Longer combat time
restrictions:
  enderpearls: true
  elytra: true
  block-buckets: true
combat-logging:
  kill-on-logout: true  # Kill combat loggers
```

### Step 2: Customize Messages

Change messages to match your server:
```yaml
messages:
  prefix: "&8[&cYourServer&8] &7"
  combat-tagged: "&cWatch out! You're in combat!"
```

### Step 3: Set Up Per-World Rules

Different rules for different worlds:
```yaml
worlds:
  world-specific:
    world:
      combat-duration: 15
    
    factions_world:
      combat-duration: 30
      restrictions:
        enderpearls: true
    
    practice:
      combat-duration: 5
      restrictions:
        enderpearls: false
```

### Step 4: Apply Changes

Reload without restart:
```
/bl reload
```

## 🎨 Visual Customization

### Change Glowing Color

```yaml
visual-effects:
  glowing:
    enabled: true
    color: YELLOW  # RED, BLUE, GREEN, YELLOW, PURPLE, PINK, WHITE
```

### Change Boss Bar Style

```yaml
visual-effects:
  boss-bar:
    enabled: true
    title: "&4💀 &lPVP MODE &4💀"
    color: RED
    style: SEGMENTED_10  # SOLID or SEGMENTED_6/10/12/20
```

### Add Particles

```yaml
visual-effects:
  particles:
    enabled: true
    type: FLAME  # FLAME, SMOKE, SPELL, HEART, etc.
    amount: 5
```

## 🚫 Blocked Actions (Default)

During combat, players cannot:
- ❌ Use ender pearls
- ❌ Use elytra
- ❌ Use /spawn, /home, /tpa commands
- ❌ Teleport to other worlds
- ❌ Enable flight
- ❌ Set bed spawn point

They CAN:
- ✅ Use /help, /rules (allowed commands)
- ✅ Fight normally
- ✅ Use potions, golden apples, etc.

## 🛡️ Permissions

### Give Staff Bypass
```yaml
permissions:
  battlelock.bypass: true  # Ignores combat restrictions
  battlelock.admin: true   # Access to all commands
```

### Regular Players
No permissions needed! Combat works automatically.

## 📊 Common Configurations

### Config 1: Standard PvP
```yaml
combat-duration: 15
restrictions:
  enderpearls: true
  elytra: true
  blocked-commands:
    - /spawn
    - /home
```

### Config 2: No-Escape PvP
```yaml
combat-duration: 20
restrictions:
  enderpearls: true
  elytra: true
  chorus-fruit: true
  disable-flight: true
  block-teleport: true
  block-buckets: true
```

### Config 3: Practice/Arena
```yaml
combat-duration: 5
restrictions:
  enderpearls: false
  elytra: false
  disable-flight: false
```

## ❓ FAQ

**Q: How do I allow /spawn after 10 seconds?**
A: Use a permission plugin to grant `battlelock.bypass` after 10s, or adjust the combat duration.

**Q: Can I have different settings in different worlds?**
A: Yes! Use the `worlds.world-specific` section in config.yml

**Q: Players are complaining about ender pearls being blocked**
A: Set `restrictions.enderpearls: false` in config.yml and `/bl reload`

**Q: How do I disable the boss bar?**
A: Set `visual-effects.boss-bar.enabled: false` and reload

**Q: What happens if someone combat logs?**
A: By default, their inventory and XP drop. Enable NPC spawning with Citizens for more options.

## 🆘 Need Help?

1. **Check the full README.md** for detailed documentation
2. **Enable debug mode** in config.yml to see what's happening
3. **Check console** for error messages
4. **Ask on Discord** or create a GitHub issue

## 🎉 You're Ready!

That's it! Your combat tagging system is now configured. Players will automatically be tagged when they enter PvP, and you can customize everything to match your server's needs.

**Pro Tip**: Test your config on a test server first, then apply to production!

---

For advanced configuration and features, see the full [README.md](README.md) file.
