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

---

<br>

## Syntax & Usage

<br>

**1. How to define a new Class**

To create a class for your objects with strict data types, use the following syntax:

```batch
%ES-engine% struct "OptMode-true/false" "ClassName" "DataType:PropertyName" "DataType:PropertyName" ... (and so on)
```
Example:
```batch
%ES-engine% struct "OptMode-true" "resources" "str:display_name" "int:price"
```
<br>

**OptMode (Optimization Mode)**

• **`"OptMode-true"`** - Speeds up processing. **NOTE:** While enabled, existing class structures are locked and cannot be updated until optimization mode is turned off. *(Recommended for release).*

• **`OptMode-false`** — Standard mode. Allows full dynamic updates and overwriting of structure blueprints on the fly. *(Recommended for debugging).*

<br>

<details>
<summary>? Frequently Asked Questions <sub>(expand)</sub></summary>
  <br>
  
#### Q: Why build an OOP engine inside Windows Batch?

**A:** Windows Batch is historically limited, lacking native support for classes, objects, and type validation. **Struct-Utility** was created to challenge
these limitations, demonstrating that with advanced scripting mechanics (like recursive token loops and variable expansion hacks), you can bring a modern,
structured architecture to vanilla CMD scripts.

<br>

#### Q: Is there really no limit to the number of class properties?

**A:** Technically, there is no hard limit—thanks to the dynamic `SHIFT` loop, you can pass 20 or more properties. However, keep in mind that **the more properties you add, the slower the class initialization becomes**. Processing a massive number of properties requires more CPU cycles and disk writes in Windows Batch, so it is recommended to keep your structs optimal and clean.

<br>

#### Q: Will this slow down my game or application during gameplay?

**A:** Reading values from an initialized entity is instant because they are loaded directly into RAM environment variables. To maximize performance during file creation, you can toggle `OptMode-true` to prevent unnecessary hard drive write cycles and use high-speed metadata caching.
</details>

<br>

**2. Instantiating an Entity**

To instantiate an entity from a defined class, use the syntax below:

```batch
%ES-engine% new "ClassName" "EntityName" "Value 1" "Value 2" ... (and so on)
```

Example:
```batch
%ES-engine% new "resources" "wood" "Pine Wood" "50"
```
<br>
<details>
<summary>★ Entity Initialization Notes:  <sub>(expand)</sub></summary>

<br>

• **Overflow Protection:** If the number of passed values exceeds the allowed property count defined in the class, the engine halts and fires Error.

• **Underflow Behavior:** If you pass fewer values than the class requires, the remaining properties will remain uninitialized (empty).

• **Variable Access Pattern:** Injected variables are stored in RAM using the following strict template: `!ClassName.EntityName.PropertyName!`

• **Object Overwriting:** Running the `new` command on an existing `EntityName` will completely overwrite its previous data.
</details>

<br>

**3. How to set up a Namespace**

To bind classes to a namespace, use the following syntax:

```batch
%ES-engine% namespace NNMode-true/false "NameSpaceName" "ClassName" "ClassName" ... (and so on)
```

Example:
```batch
%ES-engine% namespace NNMode-false "items" "resources"
```

<br>

**NNMode (Nested Namespace Mode)** 

• **`NNMode-false`** - Accepts Classes name only (reads .meta files).

• **`NNMode-true`** - Accepts Namespaces only (reads set memory).

<br>

<details>
<summary>★ Namespace Configuration Notes <sub>(expand)</sub></summary>

<br>

• **Multi-Class Binding:** You can bind multiple different classes to a single namespace within a single command call.

• **Nested / Cascading Namespaces:** The engine supports deep nesting. By executing the namespace command sequentially, you can chain multiple namespaces together to create advanced tree-like structures (e.g., `!models.items.resources.iron.price!`).

• **Deep Variable Access Pattern:** After executing the namespace command, variables become accessible via a nested structure: `!NamespaceName.ClassName.EntityName.PropertyName!`

• **Empty Class Protection:** If you try to resolve a namespace for a class that has no active initialized entities, the engine will trigger an error and halt.

</details>

---

<br>

## Practical Example

<br>

Here, I will demonstrate what kind of nested structure tree you can build, using a clear example from gamedev.

<br>
<details>
<summary> Struct-Tree <sub>(expand)</sub></summary>

<br>

```txt
📁 items 
├─➣ 📁 products
│    ├─➣ 📁 gear
│    │    ├─➣ 📐 tools
│    │    │    ├─➣ 🔹 iron_sword
│    │    │    └─➣ 🔹 iron_axe
│    │    └─➣ 📐 equipment
│    │         ├─➣ 🔹 iron_helmet
│    │         └─➣ 🔹 iron_chestplate
│    └─➣ 📁 components
│         ├─➣ 📐 parts
│         │    ├─➣ 🔹 copper_wire
│         │    └─➣ 🔹 glass
│         └─➣ 📐 artifacts
│              ├─➣ 🔹 blood_ruby
│              └─➣ 🔹 emerald
└─➣ 📁 resources
     ├─➣ 📐 raw
     │    ├─➣ 🔹 iron
     │    └─➣ 🔹 copper
     └─➣ 📐 crafted
          ├─➣ 🔹 iron
          └─➣ 🔹 copper
```
</details>

<br>

This is the type of object tree you can create by using the following syntax:

```batch
!ES-engine! struct "OptMode-true" "tools" "str:display_name" "int:count" "int:multiplier_mining_dirt" "int:multiplier_mining_stone" "int:multiplier_mining_wood" "int:multiplier_damage"
!ES-engine! struct "OptMode-true" "equipment" "str:display_name" "int:count" "int:flat_resistance_strike" "int:flat_resistance_magic"
!ES-engine! struct "OptMode-true" "parts" "str:display_name" "int:count"
!ES-engine! struct "OptMode-true" "artifacts" "str:display_name" "int:count" "str:display_rarity" "int:rarity_lvl" "int:price"
!ES-engine! struct "OptMode-true" "raw" "str:display_name" "int:smelt_time_multiplier" "int:smelt_energy_multiplier"
!ES-engine! struct "OptMode-true" "crafted" "str:display_name" "int:price"

!ES-engine! new "tools" "iron_sword" "Iron Sword" "0" "1" "1" "1" "3"
!ES-engine! new "tools" "iron_axe" "Iron Axe" "0" "1" "1" "2" "2"

!ES-engine! new "equipment" "iron_helmet" "Iron Helmet" "0" "2" "1"
!ES-engine! new "equipment" "iron_chestplate" "Iron Chestplate" "0" "5" "3"

!ES-engine! new "parts" "copper_wire" "Copper Wire" "0"
!ES-engine! new "parts" "glass" "Glass" "0"

!ES-engine! new "artifacts" "blood_ruby" "Blood Ruby" "0" "Legendary" "5" "3500"
!ES-engine! new "artifacts" "emerald" "Emerald" "0" "Epic" "4" "2700"

!ES-engine! new "raw" "iron" "Iron Ore" "5" "10"
!ES-engine! new "raw" "copper" "Copper Ore" "3" "7"

!ES-engine! new "crafted" "iron" "Iron Ingot" "300"
!ES-engine! new "crafted" "copper" "Copper Ingot" "230"

!ES-engine! namespace "NNMode-false" "gear" "equipment" "tools"
!ES-engine! namespace "NNMode-false" "components" "parts" "artifacts"
!ES-engine! namespace "NNMode-true" "products" "gear" "components"

!ES-engine! namespace "NNMode-false" "resources" "raw" "crafted"

!ES-engine! namespace "NNMode-true" "items" "resources" "products"
```
