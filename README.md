# Buniversal 🍞⇄🟢

**The universal runtime adapter for Bun.** Write once, run anywhere—whether you're in a **Bun** runtime or a **Node.js** runtime.

[![npm version](https://img.shields.io/npm/v/buniversal.svg?style=for-the-badge)](https://www.npmjs.com/package/buniversal)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](http://makeapullrequest.com)
[![Bun](https://img.shields.io/badge/Runtime-Bun&Node.js-%23000000?style=for-the-badge&logo=bun)](https://bun.sh)

## The Problem

You're building a library, tool, or script that uses the fantastic Bun API (`Bun.build`, `Bun.spawn`, etc.). But what happens when your users are in a Node.js environment? Your code breaks.

Do you maintain two separate scripts? Write complex abstraction layers? **Buniversal** solves this.

## The Solution

Buniversal provides a unified, promise-based interface for running Bun's core functionality. It automatically detects the current JavaScript runtime and uses the optimal method:

*   **In Bun:** Uses the native, lightning-fast Bun API directly (`Bun.build()`, `Bun.spawn()`).
*   **In Node.js:** Spawns a child process to execute the Bun CLI (`bun build`, `bun run`) seamlessly.

No more `if (typeof Bun !== 'undefined')` checks cluttering your code.

## Features

✨ **Runtime Agnostic:** Your code works flawlessly in both Bun and Node.js.
⚡ **Performance First:** Leverages the full power of the native Bun API when available.
🔧 **Unified API:** Simple, consistent functions for `build`, `spawn`, and `run`.
📦 **Zero Dependencies:** Keeps your project lightweight and secure.
🛡 **TypeScript Native:** Full type definitions included.

## Installation

```bash
npm install buniversal
# or
bun add buniversal
```

## Quick Start

```typescript
import { build, spawn } from 'buniversal';

// Build with Bun, anywhere
const buildResult = await build({
entrypoints: ['./src/index.ts'],
outdir: './dist',
});

// Run a script with Bun, anywhere
const { stdout, stderr, exitCode } = await spawn(['run', 'my-script.ts']);

console.log('Build success!', buildResult.outputs);
console.log('Script output:', stdout.toString());
```

## API Reference

### `build(options: BunBuildOptions)`

Executes a build operation using either `Bun.build()` (in Bun) or `bun build` CLI (in Node.js).

### `spawn(args: string[], options?: BunSpawnOptions)`

Spawns a subprocess using either `Bun.spawn()` (in Bun) or `child_process.spawn()` with Bun CLI (in Node.js).

### `run(script: string, options?: BunRunOptions)`

Runs a script using either `Bun.run()` (in Bun) or `bun run` CLI (in Node.js).

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.

1.  Fork the repo
2.  Create a feature branch (`git checkout -b feat/amazing-thing`)
3.  Commit your changes (`git commit -m 'feat: add amazing thing'`)
4.  Push to the branch (`git push origin feat/amazing-thing`)
5.  Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Buniversal** - Stop worrying about the runtime. Start building.
