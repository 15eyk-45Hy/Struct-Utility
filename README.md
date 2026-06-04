# Struct-Utility

**Structure and OOP simulation in Batch**

<br>

This utility provides a massive structural level-up, transforming standard Batch files

into a clean and well-organized environment.

---

<br>

### ◄|► Navigation


## Installation & Quick Setup

To get started, download the latest `Struct Utility.zip` from the **Releases** section. After that, follow these setup instructions:

• **1.** Extract the ZIP archive completely.

• **2.** The `Struct Utility` folder is the **core root directory** of the engine.

• **3.** Create your game folder, place the engine's root directory inside it, and create your main game file there.

<br>

⬡ **Advanced Configuration:**

If you want to place your main game file in a separate folder where the engine's root directory is **not** in the same root scope, you must change the settings parameter:
Set `SEPARATE_GAME_DIR=true` (by default, it is set to `false`).
  
<br>

###  Configuration Scenarios
Copy the initialization block into the beginning of your main script. Choose one of the 3 path scenarios below by adjusting the `SEPARATE_GAME_DIR` flag:

<br>

#### Scenario **A**: "Lazy Mode" (All-in-one directory)

*The quickest way for raw testing. Your game script is placed directly inside the utility folder next to `engine.bat`.*

▫ Settings: `set "SEPARATE_GAME_DIR=false"`

<details>
<summary>▦ View Directory Map <sub>(expand)</sub></summary>
<br>

```text
📁 Struct Utility/          ◄• Everything inside the engine folder
├─➣ 📁 DataBase-Structs/    
├─➣ 📄 engine.bat           
├─➣ 📄 ErrorProtocol.bat    
└─➣ 📄 game.bat             ◄• Your game script is dropped right here
```
</details>

<br>

#### Scenario **B**: "Simple Mode" (Standard Separation)
*Clean and organized. A main project folder holds your game script, and the utility folder sits right next to it.*

▫ Settings: `set "SEPARATE_GAME_DIR=false"`

<details>
<summary>▦ View Directory Map <sub>(expand)</sub></summary>
<br>

```text
📁 MyGameProject/           ◄• Your main project root
├─➣ 📄 game.bat              ◄• Your main game script
└─➣ 📁 Struct Utility/       ◄• The engine folder sits alongside it
```
</details>

<br>

#### Scenario **C**: "Advanced Mode" (Engine One Level Above)
*Perfect for multi-project workspaces where the engine core is completely separated from isolated game apps.*
▬
▫ Settings: `set "SEPARATE_GAME_DIR=true"`

<details>
<summary>▦ View Directory Map <sub>(expand)</sub></summary>
<br>

```text
📁 MyDeveloperWorkspace/
├─➣ 📁 Struct Utility/       ◄• Shared engine core files
└─➣ 📁 MyGame/               ◄• Isolated game folder
    └─➣ 📄 game.bat          ◄• Resolves paths upward (..) to find core
```

</details>

