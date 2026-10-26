<div align="center">

```
 ____                                            _   _
|  _ \ ___ _ __  _ __  _   ___      _____  _ __| |_| |__
| |_) / _ \ '_ \| '_ \| | | \ \ /\ / / _ \| '__| __| '_ \
|  __/  __/ | | | | | | |_| |\ V  V / (_) | |  | |_| | | |
|_|   \___|_| |_|_| |_|\__, | \_/\_/ \___/|_|   \__|_| |_|
                       |___/
```

**Your PC, explained in plain language. A discreet butler for Windows.**
*Seu PC, explicado em português claro.*

`Windows 10/11 x64` · `.NET 10` · `Avalonia` · `Native AOT` · `EN + PT-BR` · `Free`

</div>

---

## `> whoami`

> *"Sir, your C: drive is at 94%. Shall I show you what is eating the space?
> I won't delete anything without your word."*

**Pennyworth** is a free Windows app that answers, in simple language, the questions the
system never answers properly:

- **Where did my space go?** Every byte of every drive, by category, always adding up to 100%.
- **What can I safely clean?** Grouped by how safe it is, with **every file listed before**
  anything is deleted.
- **Who is slowing things down right now?** Live memory and processor usage, with human names
  for obscure Windows processes.
- **What is inside my machine?** Every part of the hardware, in plain words.
- **What if I just want to ask?** An assistant that answers from what the app *measured* on
  your PC.

## `> why`

```
  Windows Explorer              Pennyworth
  ─────────────────────         ─────────────────────────────
  Folder  ->  "Calculating..."  Folder  ->  size, sorted
  Drive   ->  a blue bar        Drive   ->  categories that add up to 100%
  Cleanup ->  "Are you sure?"   Cleanup ->  the exact list of files
  Process ->  svchost.exe       Process ->  what it actually is
```

Windows **does not show folder sizes natively**. To find out what is filling your disk you open
properties, wait, repeat, or install three more unknown programs. Pennyworth was born from
that frustration: **one honest, readable tool.**

## `> why windows first`

```
   [ Windows ]=====> [ macOS ]  [ Linux ]
       ^
     HERE                (maybe, someday)
```

The initial focus is **Windows only**, on purpose:

1. **That is where the pain is.** macOS and Linux have native ways to see folder sizes
   (`du`, Finder, desktop-environment analysers). Windows does not, which is why a whole market
   of disk analysers exists for it.
2. **Depth before breadth.** Safe cleanup, Windows process names, the Recycle Bin, Credential
   Manager and DirectML are platform-specific integrations. Doing one platform well beats doing
   three badly.
3. **It proves the idea fast.** One target, one knowledge base, one installer.

## `> features`

| Screen | What you get |
|---|---|
| `01 Home` | The state of the PC at a glance |
| `02 Storage` | Where the space on each drive goes, by category |
| `03 Cleanup` | What can be freed, grouped by safety; every file listed before deleting |
| `04 Memory & CPU` | Apps using memory and the processor right now, with plain names |
| `05 Folders` | A folder browser sorted by size |
| `06 Specs` | Every part of the PC in plain words, with "Copy all" |
| `07 Ask` | The assistant: answers from what the app measured, **never changes anything by itself** |
| `3D` | An ASCII PC you can rotate, with live status per part |

```
        .-----------------------.
       /  CPU  [####....]  41%  /|
      /  RAM  [#######.]  78%  / |
     /  GPU  [##......]  22%  /  |
    '-----------------------'   |
    |   C:  [#########.]  94% |  /
    |   D:  [###.......]  31% | /
    '-----------------------'/
```

## `> the butler (assistant)`

```
   Want to run offline?                Want to use your own AI account?
   ────────────────────                ────────────────────────────────
   Small model, on your PC             OpenAI-compatible · Anthropic
   Phi-4-mini   (GPU, 6GB+ VRAM)       Google Gemini · Azure OpenAI
   Phi-3.5-mini (CPU only)             You see exactly what will be sent
   MIT · SHA-256 verified              Your name and folders become <user>
```

- **Grounded:** the app measures the facts and applies its own diagnosis rules; the model only
  *explains* them. It can point to Pennyworth's screens, **never act on the PC**.
- **Private:** keys live in the Windows Credential Manager. Conversations stay on your PC and
  can be deleted.
- **Safe:** risky advice (editing the registry, disabling Windows Security) is replaced before
  you see it.
- **Opt-in:** nothing about the assistant runs, downloads or connects until you set it up.

## `> how to run`

**Requirements:** Windows 10/11 x64 and **.NET SDK 10.0.401** (pinned in `global.json`).

```bash
# run the app
dotnet run --project src/Pennyworth.App
```

```bash
# run the tests
dotnet test
```

```bash
# Native AOT publish (needs the Visual Studio C++ build tools)
dotnet publish src/Pennyworth.App -c Release -r win-x64 -p:PublishAot=true -o publish
```

## `> anatomy`

```
 Pennyworth.App ............... UI (Avalonia)
 ├── Core ..................... storage tree, categories, formatting
 ├── KnowledgeBase ............ bilingual data: locations, processes, cleanup and diagnosis rules
 ├── Insights ................. path classification
 ├── Scanning ................. drive scanning
 ├── Cleanup .................. measuring and cleaning, Recycle Bin
 ├── Monitoring ............... live memory/CPU/GPU and hardware specs
 └── Assistant
     ├── Providers ............ cloud chat clients, keys in the Credential Manager
     └── Local ................ model catalogue, verified download, on-PC ONNX model
```

## `> principles`

```
  [1] Show before touching      nothing is deleted without the full list
  [2] Measure, don't guess      the model explains, the app calculates
  [3] Private by default        nothing leaves the PC without you seeing it
  [4] Two real languages        EN and PT-BR, not an afterthought translation
  [5] No catch                  free and straightforward
```

---

<div align="center">

```
   Pennyworth — because every PC deserves a good butler.
```

*Fonts: Golos Text and JetBrains Mono, SIL Open Font License 1.1.*

</div>
