# SWT - WhatsApp TypeScript Wrapper

A modern TypeScript wrapper around [Baileys](https://github.com/WhiskeySockets/Baileys) WhatsApp API, providing type-safe exports and comprehensive utilities for WhatsApp automation and bot development.

## 🚀 Features

- **Type-Safe**: Full TypeScript support with complete type definitions
- **Modern DX**: ES2022 target with Node.js 20+ support
- **Baileys Integration**: Access to all Baileys WhatsApp API functionalities
- **Comprehensive Exports**: Types, utilities, and protocol definitions
- **Production Ready**: Strict TypeScript configuration for reliability

## 📦 Installation

```bash
npm install @unknownncat/swt
# or
yarn add @unknownncat/swt
# or
pnpm add @unknownncat/swt
```

## ⚙️ Requirements

- **Node.js**: >= 20.0.0
- **npm/yarn/pnpm**: Latest versions

## 🔧 Building

```bash
npm run build
```

This will compile TypeScript files to `dist/` directory with:

- ESM module output
- Type declarations
- Source maps

## 📋 Project Structure

```
src/
├── Socket/           # Socket and connection management
├── Utils/            # Utility functions
├── Types/            # TypeScript type definitions
├── Defaults/         # Default configurations
├── WABinary/         # WhatsApp binary utilities
├── WAM/              # WhatsApp media handling
├── WAUSync/          # WhatsApp user sync
└── Signal/           # Signal protocol utilities
Baileys-master/       # Baileys library integration
```

## 🎯 Usage

```typescript
import makeWASocket, {
  DisconnectReason,
  useMultiFileAuthState,
} from "@unknownncat/swt";

// Create authenticated socket
const { saveCreds, state } = await useMultiFileAuthState("./auth");
const socket = makeWASocket({ auth: state });

// Handle events
socket.ev.on("messages.upsert", async (m) => {
  console.log("Message received:", m);
});

socket.ev.on("connection.update", (update) => {
  const { connection, lastDisconnect } = update;
  if (connection === "close") {
    if (
      (lastDisconnect?.error as any)?.output?.statusCode !==
      DisconnectReason.loggedOut
    ) {
      // Reconnect
    }
  }
});
```

## 📚 Documentation

For detailed documentation and examples, refer to:

- [Baileys Repository](https://github.com/WhiskeySockets/Baileys)
- [Baileys Documentation](https://github.com/WhiskeySockets/Baileys/wiki)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

This project is an unofficial wrapper for Baileys. Please use responsibly and in accordance with WhatsApp's Terms of Service. The maintainers are not responsible for any misuse or violations.

## 🙏 Acknowledgments

- [Baileys Team](https://github.com/WhiskeySockets/Baileys) for the amazing WhatsApp API library
- All contributors and users of this project

## 📞 Support

For issues and questions:

- [GitHub Issues](https://github.com/unknownncat/swt/issues)
- Create detailed bug reports
- Check existing issues before creating duplicates

---

Made with ❤️ by [unknownncat](https://github.com/unknownncat)
