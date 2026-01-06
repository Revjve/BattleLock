# Build Instructions for BattleLock

## Prerequisites

Before building BattleLock, ensure you have:

1. **Java Development Kit (JDK) 17 or higher**
   - Download from [Adoptium](https://adoptium.net/)
   - Verify installation: `java -version`

2. **Apache Maven 3.6 or higher**
   - Download from [Maven](https://maven.apache.org/download.cgi)
   - Verify installation: `mvn -version`

## Building the Plugin

### Method 1: Using Maven (Recommended)

1. **Clone or download** the repository:
   ```bash
   git clone https://github.com/yourusername/battlelock.git
   cd battlelock
   ```

2. **Build the plugin**:
   ```bash
   mvn clean package
   ```

3. **Locate the compiled JAR**:
   - The plugin JAR will be in `target/BattleLock-1.0.0.jar`

### Method 2: Using Your IDE

#### IntelliJ IDEA

1. Open IntelliJ IDEA
2. Select `File > Open` and choose the BattleLock folder
3. Wait for Maven to import dependencies
4. Open Maven panel (View > Tool Windows > Maven)
5. Expand `BattleLock > Lifecycle`
6. Double-click `package`
7. Find JAR in `target/` folder

#### Eclipse

1. Open Eclipse
2. Select `File > Import > Maven > Existing Maven Projects`
3. Browse to BattleLock folder and click Finish
4. Right-click project > Run As > Maven build
5. Set Goals to `clean package` and click Run
6. Find JAR in `target/` folder

## Installation After Building

1. Copy `target/BattleLock-1.0.0.jar` to your server's `plugins/` folder
2. Start or restart your server
3. Configure the plugin in `plugins/BattleLock/config.yml`
4. Use `/battlelock reload` to apply changes

## Build Troubleshooting

### "JAVA_HOME is not set"
Set your JAVA_HOME environment variable:

**Windows:**
```cmd
set JAVA_HOME=C:\Path\To\JDK
```

**Linux/Mac:**
```bash
export JAVA_HOME=/path/to/jdk
```

### "Maven not found"
Ensure Maven is in your PATH:

**Windows:**
Add Maven's `bin` folder to your PATH environment variable

**Linux/Mac:**
```bash
export PATH=$PATH:/path/to/maven/bin
```

### Compilation Errors
1. Ensure you're using JDK 17 or higher
2. Delete the `target/` folder and rebuild
3. Run `mvn clean install -U` to force update dependencies

## Development Setup

### Setting up for Development

1. **Fork the repository** on GitHub
2. **Clone your fork**:
   ```bash
   git clone https://github.com/yourusername/battlelock.git
   cd battlelock
   ```

3. **Import into your IDE** (IntelliJ IDEA recommended)
4. **Install dependencies**:
   ```bash
   mvn clean install
   ```

### Running a Test Server

1. Download Paper 1.21+ from [PaperMC](https://papermc.io/downloads)
2. Create a test server folder
3. Place Paper JAR in the folder
4. Accept EULA
5. Build BattleLock and copy to `plugins/` folder
6. Start server and test

### Code Style

- Use 4 spaces for indentation
- Follow Java naming conventions
- Add Javadoc comments for public methods
- Keep methods under 50 lines when possible

## Publishing

### Creating a Release

1. Update version in `pom.xml`
2. Build the plugin: `mvn clean package`
3. Test thoroughly on a test server
4. Create a Git tag: `git tag v1.0.0`
5. Push tag: `git push origin v1.0.0`
6. Create GitHub release with the JAR

### Version Numbering

Follow Semantic Versioning (SemVer):
- **MAJOR** version for incompatible API changes
- **MINOR** version for backwards-compatible functionality
- **PATCH** version for backwards-compatible bug fixes

Example: `1.2.3`
- 1 = Major version
- 2 = Minor version
- 3 = Patch version

## Additional Resources

- [Paper Plugin Development](https://docs.papermc.io/paper/dev/getting-started)
- [Maven Guide](https://maven.apache.org/guides/getting-started/)
- [Java Documentation](https://docs.oracle.com/en/java/)

## Need Help?

If you encounter any issues during building:
1. Check the [Troubleshooting section](#build-troubleshooting)
2. Search existing [GitHub Issues](https://github.com/yourusername/battlelock/issues)
3. Create a new issue with your error message and system details
