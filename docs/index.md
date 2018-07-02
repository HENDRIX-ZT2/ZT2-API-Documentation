# Welcome to the Zoo Tycoon 2 Behavior API!

This is a reference document to help you code new and exciting behaviors without having to dig through the whole codebase to discover functions. Everything used by ZT2 is here, and often you are given examples in context.

#### Notes

- Attributes preceded by * are optional
- "" designate dummy names for entries where the tag specifies the proper name
- ? designates uncertain entries
- ! designates clear errors

#### Data types

- _string_ - Usually the name of something, like an entity or an animation. May also be special, like `subject`, `target`, `object` or `fromToken`.
- _int_ - A single integer eg. `5`, optionally prefaced with a logic component, eg. `GE 20`.
- _float_ - A single floating point number, eg. `1.5`.
- _bool - A boolean toggle, either `true` or `false`.
- (_matrix3x3_) - Matrix of 3x3 ints, rare, eg. `1 0 0, -1 0 0, 0 1 0`.

---
