# BattleLock Project Structure

This document provides an overview of the BattleLock project structure and code organization.

## 📁 Directory Structure

```
BattleLock/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── battlelock/
│       │           └── plugin/
│       │               ├── commands/          # Command handlers
│       │               │   ├── BattleLockCommand.java
│       │               │   └── CombatCommand.java
│       │               ├── config/            # Configuration management
│       │               │   └── ConfigManager.java
│       │               ├── listeners/         # Event listeners
│       │               │   ├── CombatListener.java
│       │               │   ├── LogoutListener.java
│       │               │   └── RestrictionListener.java
│       │               ├── managers/          # Core managers
│       │               │   ├── CombatManager.java
│       │               │   └── VisualManager.java
│       │               ├── models/            # Data models
│       │               │   └── CombatPlayer.java
│       │               ├── tasks/             # Scheduled tasks
│       │               │   └── CombatCheckTask.java
│       │               ├── utils/             # Utility classes
│       │               │   └── MessageUtil.java
│       │               └── BattleLock.java    # Main plugin class
│       └── resources/
│           ├── config.yml                     # Default configuration
│           └── plugin.yml                     # Plugin metadata
├── target/                                     # Compiled files (gitignored)
├── .gitignore                                  # Git ignore rules
├── BUILD_INSTRUCTIONS.md                       # Build guide
├── CHANGELOG.md                                # Version history
├── pom.xml                                     # Maven build configuration
├── QUICKSTART.md                               # Quick start guide
└── README.md                                   # Main documentation
```

## 🏗️ Architecture Overview

### Main Plugin Class
**`BattleLock.java`**
- Entry point of the plugin
- Initializes all managers and listeners
- Handles plugin enable/disable lifecycle
- Registers commands and events

### Core Components

#### 1. Managers (`managers/`)
Handle major plugin functionality:

**`CombatManager.java`**
- Tracks players in combat
- Tags/untags players
- Manages combat timers
- Provides combat status queries

**`VisualManager.java`**
- Manages glowing effects
- Spawns particles
- Controls boss bars
- Displays action bar messages
- Handles visual effect cleanup

#### 2. Listeners (`listeners/`)
React to game events:

**`CombatListener.java`**
- Detects PvP combat (player vs player)
- Handles entity damage events
- Triggers combat tagging
- Manages death events

**`RestrictionListener.java`**
- Enforces combat restrictions
- Blocks ender pearls, elytra, commands
- Prevents teleportation
- Blocks item usage during combat

**`LogoutListener.java`**
- Handles combat logging
- Drops inventory/XP on logout
- Spawns NPCs (if enabled)
- Broadcasts combat log messages

#### 3. Commands (`commands/`)
Handle player/admin commands:

**`BattleLockCommand.java`**
- Main admin command (`/battlelock`)
- Subcommands: reload, status, tag, untag, list
- Tab completion support
- Permission checking

**`CombatCommand.java`**
- Player command (`/combat`)
- Check personal combat status
- Simple, user-friendly

#### 4. Configuration (`config/`)
Manages plugin settings:

**`ConfigManager.java`**
- Loads and validates configuration
- Provides getter methods for all settings
- Handles per-world configurations
- Manages hot-reload functionality

#### 5. Models (`models/`)
Data structures:

**`CombatPlayer.java`**
- Represents a player in combat
- Stores combat duration, attacker info
- Tracks combat state and timers
- Provides combat time calculations

#### 6. Tasks (`tasks/`)
Background operations:

**`CombatCheckTask.java`**
- Runs periodically (every second)
- Checks for expired combat tags
- Auto-untags players when time expires
- Cleanup for offline players

#### 7. Utilities (`utils/`)
Helper classes:

**`MessageUtil.java`**
- Message formatting with color codes
- Component conversion for Adventure API
- Consistent message sending
- Time formatting utilities

## 🔄 Data Flow

### Combat Tag Flow
```
1. Player damages another player
   ↓
2. CombatListener detects EntityDamageByEntityEvent
   ↓
3. CombatManager.tagPlayer() called
   ↓
4. CombatPlayer created/updated with timer
   ↓
5. VisualManager.startEffects() called
   ↓
6. Visual effects start (glowing, particles, boss bar)
   ↓
7. CombatCheckTask monitors timer
   ↓
8. When timer expires: CombatManager.untagPlayer()
   ↓
9. VisualManager.stopEffects() called
   ↓
10. Player notified combat ended
```

### Restriction Flow
```
1. Player tries restricted action (e.g., /spawn)
   ↓
2. RestrictionListener intercepts event
   ↓
3. Checks if player is in combat via CombatManager
   ↓
4. If in combat: Cancel event + send message
   ↓
5. If not in combat: Allow action
```

### Combat Log Flow
```
1. Player disconnects
   ↓
2. LogoutListener.onPlayerQuit() called
   ↓
3. Check if player in combat via CombatManager
   ↓
4. If in combat:
   a. Drop inventory (if enabled)
   b. Drop experience (if enabled)
   c. Spawn NPC (if enabled)
   d. Broadcast message (if enabled)
   ↓
5. VisualManager cleanup for that player
   ↓
6. CombatManager removes player tracking
```

## 🔌 Extension Points

### Adding New Restrictions
1. Add listener method in `RestrictionListener.java`
2. Add config option in `config.yml`
3. Add getter in `ConfigManager.java`
4. Add documentation in `README.md`

### Adding New Visual Effects
1. Add effect method in `VisualManager.java`
2. Add config options in `config.yml`
3. Add getters in `ConfigManager.java`
4. Call from `VisualManager.startEffects()`

### Adding New Commands
1. Create new command class in `commands/`
2. Implement `CommandExecutor` interface
3. Register in `BattleLock.java` onEnable()
4. Add to `plugin.yml`

### Adding Database Support
1. Create `database/` package
2. Create DatabaseManager class
3. Implement connection pooling
4. Store combat logs, statistics
5. Add config options for database

## 🧪 Testing Strategy

### Unit Testing (Future)
- Test ConfigManager settings loading
- Test CombatPlayer time calculations
- Test MessageUtil formatting
- Test combat tag logic

### Integration Testing (Future)
- Test event flow (damage → tag → visual effects)
- Test command execution
- Test permission checks
- Test config reload

### Manual Testing
- Test on Paper 1.21 server
- Test all restriction types
- Test combat logging
- Test per-world configs
- Test visual effects

## 📊 Performance Considerations

### Optimization Points
1. **CombatCheckTask**: Runs every second, iterate efficiently
2. **VisualManager**: Batch particle spawning, cache boss bars
3. **ConfigManager**: Cache frequently accessed values
4. **CombatManager**: Use HashMap for O(1) lookups

### Memory Management
- Clean up combat data on player quit
- Cancel scheduled tasks properly
- Remove boss bars from players
- Clear particle tasks

## 🔐 Security Considerations

1. **Permission Checks**: Always verify permissions before actions
2. **Input Validation**: Sanitize player names in commands
3. **Event Priority**: Use appropriate priorities to avoid conflicts
4. **Config Validation**: Validate all config values on load

## 📝 Code Standards

### Naming Conventions
- **Classes**: PascalCase (e.g., `CombatManager`)
- **Methods**: camelCase (e.g., `tagPlayer`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_DURATION`)
- **Variables**: camelCase (e.g., `combatPlayer`)

### Documentation
- JavaDoc for all public methods
- Inline comments for complex logic
- README sections for user-facing features
- Code comments for non-obvious implementations

### Error Handling
- Try-catch for external API calls
- Null checks for optional values
- Graceful degradation on errors
- Informative error messages in console

## 🚀 Build Process

1. **Clean**: `mvn clean`
2. **Compile**: Java 17+ compilation
3. **Package**: Create JAR with dependencies
4. **Output**: `target/BattleLock-1.0.0.jar`

## 📦 Dependencies

### Required
- **Paper API** 1.21+ (provided by server)
- **Java** 17+ (runtime)

### Optional
- **Citizens** (for NPC spawning)
- **PlaceholderAPI** (future feature)
- **Vault** (future feature)

## 🔮 Future Enhancements

See [CHANGELOG.md](CHANGELOG.md) for planned features in upcoming versions.
