# Telegram Desktop - Project Documentation

## 📋 Project Overview

**Telegram Desktop** is the official messenger desktop application for the Telegram messaging service. This is a fork of the original Telegram Desktop codebase, providing a complete source implementation of the desktop client based on the Telegram API and the MTProto secure protocol.

### Key Information
- **Project Type**: Cross-platform desktop messaging application
- **License**: GPLv3 with OpenSSL exception
- **Repository**: Based on official Telegram Desktop (https://github.com/telegramdesktop/tdesktop)
- **Build System**: CMake (version 3.25 or higher)
- **Languages**: C++ (primary), with C support
- **Supported Platforms**: Windows, macOS (Intel & ARM), Linux

### Supported Systems
- **Windows**: 7 and above (32-bit and 64-bit)
- **macOS**: 10.13 and above (Intel and ARM64)
- **Linux**: Static build for 64-bit systems, Snap and Flatpak support

---

## 📁 Project Structure

### Root Directory (`tdesktop/`)
```
tdesktop/
├── .agents/                  # Agent configuration files for AI/automation
├── .claude/                  # Claude editor configuration
├── .github/                  # GitHub workflows and contributing guidelines
├── Telegram/                 # Main application source code
├── cmake/                    # CMake configuration files
├── docs/                     # Documentation and build guides
├── lib/                      # Third-party and custom library dependencies
├── build/                    # Build-related files (generated during build)
├── changelog.txt             # Version history and changes
├── LICENSE                   # GPLv3 license with OpenSSL exception
├── README.md                 # Official project README
├── CMakeLists.txt           # Root CMake configuration
└── .devcontainer.json       # Docker development container configuration
```

---

## 🏗️ Detailed Directory Structure

### 1. **Telegram/ Directory** - Main Source Code
The core application source code is organized by functionality:

```
Telegram/
├── SourceFiles/              # C++ source files (.cpp)
├── build/                    # Build scripts and configuration
│   └── version               # Version information
├── cmake/                    # CMake build definitions
├── codegen/                  # Code generation tools
├── Resources/                # Application resources (icons, assets)
├── create.bat                # Windows build script
├── configure.bat             # Windows configuration script
├── configure.sh              # Unix configuration script
├── configure.py              # Python configuration utility
└── CMakeLists.txt           # Telegram subdirectory CMake config
```

#### Main Source Directories (`SourceFiles/`)
```
SourceFiles/
├── ui/                       # User interface components
├── core/                     # Core application logic
├── data/                     # Data models and structures
├── window/                   # Window management
├── calls/                    # Voice/video calling functionality
├── history/                  # Chat history management
├── dialogs/                  # Dialog/chat management
├── boxes/                    # Dialog boxes and popups
├── chat_helpers/             # Chat-related utilities
├── api/                      # Telegram API integration
├── storage/                  # Local data storage
├── mtproto/                  # MTProto protocol implementation
├── base/                     # Base classes and utilities
├── payments/                 # Payment processing (Telegram Payments)
├── settings/                 # Application settings
├── editor/                   # Text/code editor components
├── media/                    # Media handling (audio, video, images)
├── intro/                    # Onboarding/intro screens
├── auth/                     # Authentication logic
└── platform/                 # Platform-specific code
    ├── win/                  # Windows-specific implementation
    ├── mac/                  # macOS-specific implementation
    └── linux/                # Linux-specific implementation
```

### 2. **Libraries (lib/) Directory**
Custom and third-party libraries used by the application:

```
lib/
├── lib_base/                 # Base utilities and common functions
│   ├── base/
│   ├── types/
│   └── variant/
├── lib_crl/                  # Collection library (custom implementation)
├── lib_lottie/               # Lottie animations support
├── lib_qr/                   # QR code generation
├── lib_rpl/                  # Reactive programming library
├── lib_spellcheck/           # Spell checking functionality
├── lib_storage/              # Custom storage/serialization
├── lib_tl/                   # TL (Type Language) schema definitions
├── lib_translate/            # Translation/localization
├── lib_ui/                   # UI components and widgets
├── lib_webrtc/               # WebRTC for voice/video calls
└── lib_webview/              # Web view component
```

### 3. **Build System (cmake/) Directory**
```
cmake/
├── validate_special_target.cmake   # Build target validation
├── version.cmake                   # Version parsing and management
├── tests.cmake                     # Test configuration
└── [other build configurations]
```

### 4. **Documentation (docs/) Directory**
```
docs/
├── building-win.md           # Windows build instructions
├── building-mac.md           # macOS build instructions
├── building-mas.md           # macOS App Store build guide
├── building-linux.md         # Linux build instructions
├── api_credentials.md        # API credentials setup guide
├── misc.txt                  # Miscellaneous documentation
└── assets/                   # Documentation images and assets
```

### 5. **Resources Directory**
```
Telegram/Resources/
├── default_shortcuts-custom.json   # Custom keyboard shortcuts
├── images/                         # UI images and icons
├── fonts/                          # Application fonts
├── qss/                            # Qt stylesheets
└── other_resource_files
```

---

## 🔧 Build System

### Build Configuration

The project uses **CMake** as its primary build system with a specific directory structure expected:

```
L:\Telegram\                    # BuildPath (root)
├── tdesktop\                  # Repository (working directory)
├── Libraries\                 # 32-bit dependencies (Linux/macOS)
├── win64\Libraries\           # 64-bit dependencies (Windows)
└── ThirdParty\                # Build tools (NuGet, Python, etc.)
```

### Build Commands

From repository root:


```bash
cmake --build out --config Debug --target Telegram
```

The output executable will be located at: `out/Debug/Telegram.exe`

### Platform-Specific Requirements

#### Windows
- **Requirements**: Visual Studio 2022
- **Native Tools Command Prompt**: 
  - `x64 Native Tools Command Prompt` for 64-bit builds
  - `x86 Native Tools Command Prompt` for 32-bit builds
  - `ARM64 Native Tools Command Prompt` for ARM64 builds
- **Dependencies**: `../win64/Libraries` (64-bit) or `../Libraries` (32-bit)

#### macOS
- **Requirements**: Xcode
- **Dependencies**: `../Libraries/local/Qt-*`

#### Linux
- **Requirements**: GCC/Clang with development libraries
- **Docker Support**: Use `.devcontainer.json` for containerized development

---

## 📚 Third-Party Dependencies

The project uses various open-source libraries:

- **Qt 6** and **Qt 5.15** - UI framework (LGPL)
- **OpenSSL 3.2.1** - Cryptography (Apache License 2.0)
- **WebRTC** - Voice/video calling (New BSD License)
- **zlib** - Compression (zlib License)
- **LZMA SDK 9.20** - Compression (public domain)
- **FFmpeg** - Media processing (LGPL)
- **OpenAL Soft** - Audio (LGPL)
- **Opus codec** - Audio codec (BSD License)
- **Google Breakpad/Crashpad** - Crash reporting (Apache License 2.0)
- **Hunspell** - Spell checking (LGPL)
- **Ada** - URL parsing (Apache License 2.0)
- **QR Code generator** - QR codes (MIT License)
- And many others...

---

## 🎯 Key Features & Components

### Core Features
1. **Messaging**
   - Instant messaging (one-to-one and groups)
   - Channel creation and management
   - Message editing and deletion
   - Reactions and emojis

2. **Voice & Video**
   - Voice calls (using WebRTC)
   - Video calls
   - Screen sharing
   - Call recording

3. **Media Support**
   - Image viewing and sharing
   - Video playback
   - Document handling
   - Animated sticker support (via Lottie)

4. **User Features**
   - User authentication (phone-based)
   - Profile management
   - Settings and preferences
   - Two-factor authentication support

5. **Security**
   - End-to-end encryption for Secret Chats
   - MTProto secure protocol
   - OpenSSL integration for cryptography
   - Crash reporting via Crashpad

6. **Advanced Features**
   - Bot integration
   - Payment processing (Telegram Payments)
   - Message search and history
   - Spell checking
   - Translation support
   - Custom themes and styling

---

## 🔑 Important Files

| File | Purpose |
|------|---------|
| `CMakeLists.txt` | Root CMake configuration |
| `README.md` | Official project introduction |
| `LICENSE` | GPLv3 license with OpenSSL exception |
| `AGENTS.md` | Agent/automation configuration guide |
| `REVIEW.md` | Code review guidelines |
| `.devcontainer.json` | Docker development environment setup |
| `changelog.txt` | Version history and release notes |

---

## 📊 Project Statistics

- **Source Files**: ~1,144 C++ files
- **Languages**: C++ (primary), C, Objective-C (macOS specific)
- **Build System**: CMake
- **Total Dependencies**: 20+ third-party libraries

---

## 🚀 Development Workflow

### Setup Process
1. Clone the repository
2. Install platform-specific dependencies
3. Run configuration script (`configure.bat` or `configure.sh`)
4. Build using CMake: `cmake --build out --config Debug --target Telegram`
5. Run the executable from `out/Debug/`

### Build Variants
- **Debug**: For development and testing (recommended)
- **Release**: For production (very heavy, not recommended for testing)

### Configuration
- Platform-specific configuration in `Telegram/configure.*` scripts
- Build options stored in CMake cache
- Cross-platform build support with platform-specific fallbacks

---

## 📖 Documentation

Additional documentation is available in:
- `docs/building-win.md` - Detailed Windows build guide
- `docs/building-mac.md` - Detailed macOS build guide
- `docs/building-mas.md` - Mac App Store specific guide
- `docs/building-linux.md` - Linux build guide
- `docs/api_credentials.md` - API setup documentation

---

## 🔗 Project Links

- **Official Repository**: https://github.com/telegramdesktop/tdesktop
- **Telegram**: https://telegram.org
- **Desktop App**: https://desktop.telegram.org
- **Telegram API**: https://core.telegram.org
- **MTProto Protocol**: https://core.telegram.org/mtproto

---

## 📝 License

This project is published under the **GPLv3 with OpenSSL exception**. See the `LICENSE` file for full details.

---

## 🤝 Contributing

Contributions are welcome! Please refer to:
- `.github/CONTRIBUTING.md` for contribution guidelines
- `REVIEW.md` for code review standards
- Build instructions for your platform

---

## 💡 Notes for Development

- Always use **Debug builds** for development
- Keep dependencies in the expected directory structure
- Use platform-specific Native Tools Command Prompt on Windows
- Refer to `AGENTS.md` for automation and CI/CD guidelines
- Check `.devcontainer.json` for containerized development options

---

*This documentation was auto-generated on 2026-05-26 as part of the Telegram Desktop Fork project analysis.*
