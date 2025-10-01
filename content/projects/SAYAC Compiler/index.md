---
title: "SAYAC Compiler"
weight: 1
#date: 2023-02-01
tags: ["Compiler","C ","java", "antlr"]
author: ["By: Rayhaneh Einollahi, Bahareh Einollahi, Mahdis Mirzaei, Hasti Aboalhasani"]
description: "Simple C Compiler in Java Designed For SAYAC Proccessor" 
summary: "Simple C Compiler in Java Designed For SAYAC Proccessor" 
cover:
  image: "image.jpg"
  alt: "image"
  relative: false
#editPost:
 #   URL: "https://doi.org/10.1073/pnas.1816454115"
 #   Text: "Other Journal Name"

---
**Supervisor:** Professor Navabi

---

## Overview

The SAYAC compiler translates **Mini-C ASTs** into **SAYAC assembly**. Its backend consists of:

- **Memory Manager:** Handles globals, locals, temps, stack frames, and alignment.
- **Register Manager:** Allocates CPU registers, handles spills/reloads.
- **Instruction Emitter:** Generates SAYAC syntax for ALU, memory, and control operations.
- **Code Generator:** Handles main conversion of AST nodes to assembly.

```c
int main() {
    int i;
    for (i = 0; i < 5; i++) {
        if (i == 3) break;
    }
    return 0;
}
```

```asm
func_main:
    STR FP SP
    ADR ZR SP FP
    ADI -2 SP
    MSI 0 R1
    ADI -2 R2
    LDR FP R2
    ADI 2 R2
for_condition_0:
    CMI 5 R1
    BRR gt for_body_1
    JMP for_end_2
for_body_1:
    CMI 3 R1
    BRR eq If_4
    JMP After_If_6
If_4:
    JMP for_end_2
    JMP After_If_6
After_If_6:
    JMP for_step_3
for_step_3:
    ADR ZR R1 R2
    ADI 1 R1
    JMP for_condition_0
for_end_2:
    MSI 0 R3
    ADR ZR R3 RT
    JMP func_ret_main
func_ret_main:
    ADR ZR FP SP
    LDR FP FP
    JMR 0 RA R0
```
---
<a href="https://github.com/Rayhaneh-Einollahi/SAYAC_Compiler" target="_blank" rel="noopener" 
   style="display:inline-block; padding:12px 24px; font-weight:bold; background-color:#24292e; 
          color:white; border-radius:8px; text-decoration:none; font-size:16px;">
  ⭐ Star on GitHub
</a>

---


