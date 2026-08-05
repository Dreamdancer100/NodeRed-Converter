🌍 Sprachen: [🇺🇸 English](https://github.com/Dreamdancer100/NodeRed-Converter/blob/main/README.md) | [🇩🇪 Deutsch](https://github.com/Dreamdancer100/NodeRed-Converter/blob/main/README.de.md#)

<div align="center">

<img src="./nodered.png" alt="NodeRed-Converter" width="48" />

# NodeRed-Converter #

### ioBroker → Marc-Berg Node-RED Converter · Windows GUI

*Convert Node-RED flows built with ioBroker's standard nodes into Marc Berg's native WebSocket node format — one click, done.* ⚡

![Platform](https://img.shields.io/badge/platform-Windows-0078D6)
![Type](https://img.shields.io/badge/type-Desktop%20GUI-red)
![Made by](https://img.shields.io/badge/made%20by-Dreamdancer100-8b0000)

<img src="./background.jpg" alt="Node-RED" width="320" />

</div>

---

## ✨ What it does

If you run **Node-RED as an adapter *inside* ioBroker**, your flows use the built-in `node-red-contrib-iobroker` nodes. But the moment Node-RED runs **standalone** (its own VM / LXC / Docker) and talks to ioBroker over **WebSocket**, you need **Marc Berg's external nodes** ([`Marc-Berg/node-red-contrib-iobroker`](https://github.com/Marc-Berg/node-red-contrib-iobroker)).

**NodeRed-Converter** takes an exported flow `.json` and rewrites it into that native WebSocket format automatically — including a matching `iob-config` connection node. 🔁

### 🔀 Node mapping

| ioBroker node | ➜ | Marc-Berg node |
|:---|:---:|:---|
| `ioBroker in`     | ➜ | `iobin` |
| `ioBroker get`    | ➜ | `iobget` |
| `ioBroker out`    | ➜ | `iobout` |
| `ioBroker sendTo` | ➜ | `iobsendto` |

➕ A fitting **`iob-config`** connection node is added automatically.

---

## 📦 Installation

1. ⬇️ Download **`NodeRed-Converter.exe`** (full installer setup) from the [Releases](../../releases).
2. 🖱️ Run it — just install the program.
3. 🔗 You'll get a **desktop shortcut**. Click it and the program opens.

### 🗂️ First launch — auto-created folders & config

On the **first start**, the program automatically creates the two folders and the config file:

```
C:\Users\<YourName>\Converter\
├── 📁 Original JSON\        ← put your source flows here
├── 📁 Konvertierte JSON\    ← converted results land here
└── 📄 config.json           ← your saved bridge settings
```

> ✅ No manual setup — it just appears.

<div align="center">
<img src="./folders.png" alt="Created folders and config file" width="560" />
<br><em>Created folders & config file</em>
</div>

---

## ⚙️ Configuration (one time)

At the top of the window, fill in the **Bridge configuration** once and click **"Konfiguration speichern"**. These values are stored in `config.json` and reused for every future conversion.

| Field | Meaning |
|:---|:---|
| 🆔 **Server-ID** | ⚠️ **Not** a free name — it must be the **exact internal Node-RED ID** of the target config node (e.g. `a1b2c3d4e5f6…`). Use the **"Vorhandene abrufen…"** button to fetch it automatically instead of guessing. |
| 🖥️ **ioBroker Host** | IP or hostname of your ioBroker server. |
| 🔌 **ioBroker Port** | Port of the ioBroker **admin adapter** instance used for the Node-RED bridge. |
| 🏷️ **Servername** | Display name for the connection in the Node-RED editor. |
| 🔒 **SSL verwenden** | Enable if your admin adapter runs on **HTTPS / WSS**. |
| 💬 **Telegram-Adapter / Method** | Only relevant if your flow uses `ioBroker sendTo` for Telegram (e.g. `telegram.1` / `send`). |
| 🌐 **Node-RED Host / Port** | The **Node-RED editor** itself (default port `1880`) — **not** the ioBroker admin instance. Used only for the *"Vorhandene abrufen…"* button. |

<div align="center">
<img src="./program-view.png" alt="Program view" width="620" />
<br><em>Program view</em>
</div>

---

## 🚀 Usage

1. 📥 Click **"JSON importieren…"** and choose one or more `flows.json` files (or exported tabs as JSON). They are copied into **Original JSON** automatically.
   *Alternatively:* drop files into the folder manually and hit **"Aktualisieren"**.
2. 🖱️ Select a file in the list, then click **"Konvertieren"**.
3. ✅ The result is written as **`<name>_Neu.json`** into **Konvertierte JSON**.
4. 📊 The bottom panel shows the **statistics** — how many `iobin` / `iobget` / `iobout` / `iobsendto` nodes were created, plus **warnings** (e.g. `DEADBAND` nodes that can't be mapped 1:1).

> ℹ️ A `Readme` text file with the same instructions ships inside the program folder — identical to the in-app **Help**.

---

## ⚠️ Notes

- **DEADBAND** nodes are flagged in the statistics because they can't be transferred 1:1 — check those manually.
- The **Server-ID** is the #1 thing people get wrong. If the new nodes show *"No server config"* in Node-RED even with *"create connection node"* checked, your Server-ID doesn't match a real config node. Use **"Vorhandene abrufen…"**.

---

## 💡 Why I built it

This program saved me a *ton* of time converting **79 flows** — some with **9,000 lines** of code. The converter runs the JSON through once and the conversion is done. 🎉

*Have fun converting your flows!* 🙌

---

## 🔗 More about this app

👉 **[Node-RED Converter on gordonx.de](https://gordonx.de/nodered-converter/)** — description, screenshots and download.

<div align="center">

Made with ❤️ by **Gordon Lehmann**

</div>
