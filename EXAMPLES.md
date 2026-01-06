# BattleLock Configuration Examples

This file contains complete, ready-to-use configuration examples for different server types.

## 📋 Table of Contents

1. [Standard PvP Server](#1-standard-pvp-server)
2. [Hardcore Survival](#2-hardcore-survival)
3. [Practice/Arena Server](#3-practicearena-server)
4. [Faction Server](#4-faction-server)
5. [Minigame Server](#5-minigame-server)
6. [SMP with Safe Zones](#6-smp-with-safe-zones)

---

## 1. Standard PvP Server

**Description**: Balanced settings for a typical PvP server with moderate restrictions.

```yaml
combat-duration: 15
debug: false

restrictions:
  enderpearls: true
  elytra: true
  chorus-fruit: true
  blocked-items:
    - ENDER_PEARL
    - CHORUS_FRUIT
  blocked-commands:
    - /spawn
    - /home
    - /tpa
    - /warp
  allowed-commands:
    - /help
    - /rules
    - /discord
  disable-flight: true
  block-teleport: true

visual-effects:
  glowing:
    enabled: true
    color: RED
  particles:
    enabled: true
    type: FLAME
    amount: 3
    interval: 20
  action-bar:
    enabled: true
    format: "&c⚔ Combat: &e{time}s &c⚔"
    update-interval: 10
  boss-bar:
    enabled: true
    title: "&c⚔ &lCOMBAT MODE &c⚔"
    color: RED
    style: SOLID
    show-timer: true

combat-logging:
  enabled: true
  spawn-npc: false
  kill-on-logout: false
  broadcast: true
  broadcast-message: "&c{player} &7combat logged!"
  drop-inventory: true
  drop-experience: true

messages:
  prefix: "&8[&cBattleLock&8] &7"
  combat-tagged: "&cYou are now in combat! Do not log out for &e{time}s&c!"
  combat-expired: "&aYou are no longer in combat."
  action-denied: "&cYou cannot do that while in combat!"
  command-blocked: "&cYou cannot use that command while in combat!"
  item-blocked: "&cYou cannot use that item while in combat!"

worlds:
  enabled-worlds:
    - world
    - world_nether
    - world_the_end

advanced:
  tag-on-mob-hit: false
  tag-on-mob-damage: false
  remove-on-death: true
  block-bed-set: true
  block-buckets: true
  minimum-damage: 0.5
  block-item-drop: false
  block-item-pickup: false
```

---

## 2. Hardcore Survival

**Description**: Strict settings for hardcore survival servers with severe penalties.

```yaml
combat-duration: 30
debug: false

restrictions:
  enderpearls: true
  elytra: true
  chorus-fruit: true
  blocked-items:
    - ENDER_PEARL
    - CHORUS_FRUIT
    - ENDER_EYE
  blocked-commands:
    - /spawn
    - /home
    - /tpa
    - /tpaccept
    - /warp
    - /back
    - /tp
    - /teleport
  allowed-commands:
    - /help
    - /rules
  disable-flight: true
  block-teleport: true

visual-effects:
  glowing:
    enabled: true
    color: YELLOW
  particles:
    enabled: true
    type: FLAME
    amount: 5
    interval: 15
  action-bar:
    enabled: true
    format: "&4⚠ &cCOMBAT &4⚠ &e{time}s"
    update-interval: 5
  boss-bar:
    enabled: true
    title: "&4💀 &lHARDCORE COMBAT &4💀 &e{time}s"
    color: RED
    style: SEGMENTED_10
    show-timer: true

combat-logging:
  enabled: true
  spawn-npc: true
  npc-duration: 60
  npc-vulnerable: true
  kill-on-logout: true
  broadcast: true
  broadcast-message: "&4[COMBAT LOG] &c{player} &4logged during combat and has been eliminated!"
  drop-inventory: true
  drop-experience: true

messages:
  prefix: "&4[&c⚠&4] &7"
  combat-tagged: "&4&l⚠ WARNING ⚠\n&cYou are in combat for &e{time} seconds&c!\n&cLogging out will result in DEATH!"
  combat-expired: "&a&lSAFE &7- You are no longer in combat."
  action-denied: "&4&lDENIED! &cYou cannot do that in combat!"
  command-blocked: "&4&lDENIED! &cNo commands during combat!"
  item-blocked: "&4&lDENIED! &cYou cannot use that item!"

worlds:
  enabled-worlds:
    - world
    - world_nether
    - world_the_end

advanced:
  tag-on-mob-hit: false
  tag-on-mob-damage: false
  remove-on-death: true
  block-bed-set: true
  block-buckets: true
  minimum-damage: 1.0
  block-item-drop: true
  block-item-pickup: false
```

---

## 3. Practice/Arena Server

**Description**: Minimal restrictions for practice servers and PvP arenas.

```yaml
combat-duration: 5
debug: false

restrictions:
  enderpearls: false
  elytra: false
  chorus-fruit: false
  blocked-items: []
  blocked-commands:
    - /spawn
  allowed-commands:
    - /help
    - /rules
    - /kit
    - /duel
  disable-flight: false
  block-teleport: false

visual-effects:
  glowing:
    enabled: true
    color: GREEN
  particles:
    enabled: false
  action-bar:
    enabled: true
    format: "&a⚔ &7Combat: &e{time}s"
    update-interval: 10
  boss-bar:
    enabled: false

combat-logging:
  enabled: false
  spawn-npc: false
  kill-on-logout: false
  broadcast: false
  drop-inventory: false
  drop-experience: false

messages:
  prefix: "&8[&aPractice&8] &7"
  combat-tagged: "&aIn combat for &e{time}s"
  combat-expired: "&7Combat ended."
  action-denied: "&cCannot do that in combat!"
  command-blocked: "&cCannot use that command!"

worlds:
  enabled-worlds:
    - arena
    - practice
    - duels

advanced:
  tag-on-mob-hit: false
  tag-on-mob-damage: false
  remove-on-death: true
  block-bed-set: false
  block-buckets: false
  minimum-damage: 0.1
  block-item-drop: false
  block-item-pickup: false
```

---

## 4. Faction Server

**Description**: Settings optimized for faction warfare with per-world rules.

```yaml
combat-duration: 20
debug: false

restrictions:
  enderpearls: true
  elytra: true
  chorus-fruit: true
  blocked-items:
    - ENDER_PEARL
    - CHORUS_FRUIT
  blocked-commands:
    - /spawn
    - /f home
    - /home
    - /tpa
    - /wild
  allowed-commands:
    - /f
    - /faction
    - /help
  disable-flight: true
  block-teleport: true

visual-effects:
  glowing:
    enabled: true
    color: PURPLE
  particles:
    enabled: true
    type: SPELL
    amount: 4
    interval: 20
  action-bar:
    enabled: true
    format: "&5⚔ &dWAR MODE &5⚔ &e{time}s"
    update-interval: 10
  boss-bar:
    enabled: true
    title: "&5⚔ &lFACTION WAR &5⚔"
    color: PURPLE
    style: SEGMENTED_20
    show-timer: true

combat-logging:
  enabled: true
  spawn-npc: true
  npc-duration: 45
  npc-vulnerable: true
  kill-on-logout: false
  broadcast: true
  broadcast-message: "&5{player} &7logged during faction combat!"
  drop-inventory: true
  drop-experience: true

messages:
  prefix: "&8[&5Factions&8] &7"
  combat-tagged: "&5You're in faction combat! &e{time}s &5remaining!"
  combat-expired: "&aYou may now leave safely."
  action-denied: "&cBlocked during faction war!"
  command-blocked: "&cNo teleporting during war!"

worlds:
  world-specific:
    world:
      combat-duration: 20
      restrictions:
        enderpearls: true
        elytra: true
    
    warzone:
      combat-duration: 30
      restrictions:
        enderpearls: true
        elytra: true
        block-buckets: true
      visual-effects:
        glowing:
          color: RED
    
    safezone:
      combat-duration: 5
      restrictions:
        enderpearls: false
        elytra: false

advanced:
  tag-on-mob-hit: false
  tag-on-mob-damage: false
  remove-on-death: true
  block-bed-set: true
  block-buckets: true
  minimum-damage: 0.5
  block-item-drop: true
  block-item-pickup: false
```

---

## 5. Minigame Server

**Description**: Quick combat tags for minigames like Bedwars, Skywars, etc.

```yaml
combat-duration: 3
debug: false

restrictions:
  enderpearls: false
  elytra: false
  chorus-fruit: false
  blocked-items: []
  blocked-commands:
    - /lobby
    - /hub
    - /leave
  allowed-commands:
    - /help
    - /stats
  disable-flight: false
  block-teleport: true

visual-effects:
  glowing:
    enabled: true
    color: BLUE
  particles:
    enabled: true
    type: HEART
    amount: 2
    interval: 30
  action-bar:
    enabled: true
    format: "&b⚔ &e{time}s"
    update-interval: 10
  boss-bar:
    enabled: false

combat-logging:
  enabled: false
  spawn-npc: false
  kill-on-logout: false
  broadcast: false
  drop-inventory: false
  drop-experience: false

messages:
  prefix: "&8[&bGame&8] &7"
  combat-tagged: "&bFighting! &e{time}s"
  combat-expired: "&7Safe."
  action-denied: "&cWait!"
  command-blocked: "&cNot now!"

worlds:
  enabled-worlds:
    - bedwars
    - skywars
    - uhc
    - battleroyale

advanced:
  tag-on-mob-hit: false
  tag-on-mob-damage: false
  remove-on-death: true
  block-bed-set: false
  block-buckets: false
  minimum-damage: 0.1
  block-item-drop: false
  block-item-pickup: false
```

---

## 6. SMP with Safe Zones

**Description**: Different rules for spawn (safe), survival (normal), and PvP zones (strict).

```yaml
combat-duration: 15
debug: false

restrictions:
  enderpearls: true
  elytra: true
  chorus-fruit: true
  blocked-items:
    - ENDER_PEARL
    - CHORUS_FRUIT
  blocked-commands:
    - /spawn
    - /home
    - /tpa
  allowed-commands:
    - /help
    - /rules
    - /shop
  disable-flight: true
  block-teleport: true

visual-effects:
  glowing:
    enabled: true
    color: RED
  particles:
    enabled: true
    type: FLAME
    amount: 3
    interval: 20
  action-bar:
    enabled: true
    format: "&c⚔ Combat: &e{time}s &c⚔"
    update-interval: 10
  boss-bar:
    enabled: true
    title: "&c⚔ &lCOMBAT &c⚔"
    color: RED
    style: SOLID
    show-timer: true

combat-logging:
  enabled: true
  spawn-npc: false
  kill-on-logout: false
  broadcast: true
  broadcast-message: "&c{player} &7combat logged!"
  drop-inventory: true
  drop-experience: true

messages:
  prefix: "&8[&6SMP&8] &7"
  combat-tagged: "&cYou're in combat for &e{time}s&c!"
  combat-expired: "&aYou're safe now."
  action-denied: "&cCannot do that in combat!"
  command-blocked: "&cCannot use that command!"

worlds:
  use-blacklist: true
  disabled-worlds:
    - lobby
    - spawn
    - creative
  
  world-specific:
    world:
      combat-duration: 15
      restrictions:
        enderpearls: true
        elytra: false
    
    pvp:
      combat-duration: 25
      restrictions:
        enderpearls: true
        elytra: true
        block-buckets: true
      visual-effects:
        glowing:
          color: YELLOW
      combat-logging:
        kill-on-logout: true
    
    resource_world:
      combat-duration: 10
      restrictions:
        enderpearls: false
        elytra: false

advanced:
  tag-on-mob-hit: false
  tag-on-mob-damage: false
  remove-on-death: true
  block-bed-set: true
  block-buckets: false
  minimum-damage: 0.5
  block-item-drop: false
  block-item-pickup: false
```

---

## 🎯 Quick Customization Tips

### Adjust Combat Duration
```yaml
combat-duration: 10  # seconds
```
- **Short (5s)**: Minigames, practice
- **Medium (15s)**: Standard PvP
- **Long (30s)**: Hardcore, factions

### Enable/Disable Ender Pearls
```yaml
restrictions:
  enderpearls: true   # blocked
  enderpearls: false  # allowed
```

### Change Visual Style
```yaml
visual-effects:
  glowing:
    color: BLUE        # Change color
  boss-bar:
    style: SEGMENTED_10  # Change style
```

### Combat Logging Penalties
```yaml
combat-logging:
  kill-on-logout: true      # Kill player
  drop-inventory: true       # Drop items
  spawn-npc: true           # Spawn NPC
```

---

## 💡 Mix and Match

Feel free to combine elements from different examples:
- Use hardcore restrictions with minigame duration
- Use practice visuals with standard restrictions
- Mix per-world configs from different examples

## 🔄 Testing Your Config

1. Copy the example you want
2. Paste into `config.yml`
3. Use `/bl reload` to test
4. Adjust as needed
5. Test in-game before going live

---

For more information, see the main [README.md](README.md) file.
