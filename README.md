# GhidraReconstruct 🛡️

**GhidraReconstruct** is a universal, platform-agnostic AI agent skill (`.md`) designed to transform raw, messy Ghidra pseudo-C output into clean, standard, and fully compilable C code—**preserving 100% of the original binary logic**.

Optimized for **Claude Code, Cursor, Cline, OpenAI Codex,** and LLM web interfaces.

---

## 🚀 Why Use GhidraReconstruct?

- **Zero Logic Alteration:** Strictly forces the LLM to preserve bitwise operations, loops, and conditional flow.
- **Compilability Focused:** Strips away compiler artifacts (`in_FS_OFFSET`, `__stack_chk_fail`) and maps `undefinedX` primitives to standard `<stdint.h>` types.
- **Token & Cost Optimized:** Short, punchy, and explicit instructions prevent the model from wasting tokens on conversational preambles or explanations.

---

## 🛠️ How to Use

1. Copy the `GhidraReconstruct.md` file into your project's root directory (or append it to your `.cursorrules` / agent system instructions).
2. Feed your exported Ghidra pseudo-C file to your AI agent.
3. Trigger the skill with a simple prompt:
   > *"Read the exported Ghidra C file and apply the `GhidraReconstruct` skill rules to rewrite it into a perfectly compilable C file."*

---

## 📦 The Skill (`GhidraReconstruct.md`)

```markdown
# SKILL: Universal Ghidra Pseudo-C Code Reconstruction

## ROLE
You are a Senior Reverse Engineering and Compiler Expert with 25 years of experience.

## OBJECTIVE
Your sole task is to read the raw pseudo-C code exported from Ghidra and reconstruct it into clean, readable, and perfectly compilable standard C code that performs **THE EXACT SAME FUNCTIONALITY** as the compiled binary.

## STRICT EXECUTION RULES
1. **Zero Logic Change:** Retain 100% of the original mathematical logic, bitwise operations, if-else/switch conditions, and loop structures. The output behavior must mirror the original binary perfectly.
2. **Strip Artifacts:** Safely eliminate compiler-generated stack protections (e.g., `in_FS_OFFSET`, `local_10 = *(int *)(in_FS_OFFSET + 0x28)`, `__stack_chk_fail()`) and alignment padding.
3. **Standardize Types:** Convert Ghidra-specific primitives to standard `<stdint.h>` equivalents:
   - `undefined`, `undefined1` -> `uint8_t` or `char`
   - `undefined2` -> `uint16_t`
   - `undefined4` -> `uint32_t` or `int`
   - `undefined8` -> `uint64_t`
4. **Contextual Renaming:** Iner variables' and functions' purposes based on code flow. Rename generic terms (e.g., `uVar1`, `pvVar2`, `FUN_00401230`) into meaningful names (e.g., `buffer`, `key`, `index`, `decrypt_data`).

## OUTPUT FORMAT
- Do not engage in casual chat, preambles, or line-by-line explanations.
- Output **ONLY** the fully refactored, compilable, clean C code inside a single markdown code block (```c).
\```
```

---

## 📝 License
MIT License. Feel free to contribute and give a ⭐ if this saved your reverse engineering workflow!
