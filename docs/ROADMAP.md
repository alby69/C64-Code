# ROADMAP — C64-Code / readycode-py

## Vision
`readycode-py` serves as the Python foundation for the **C64-Intelligence-SDK** toolkit. It enables modern Python applications to interact with Commodore 64 files, disk images, BASIC programs, and hardware bridges (VICE emulator and C64 Ultimate).

The vision is to offer a modular, robust, and clean Python library and CLI tool that simplifies C64 software development, retrocomputing workflows, and hardware automation.

---

## Breve Termine (v1.x)
- **Refactoring & Architecture**: Apply KISS, DRY, and decoupling principles across `cli.py`, `diskimage.py`, and `tokenizer.py`.
- **Test Coverage**: Maintain and expand comprehensive test coverage (`pytest`) for disk manipulation, tokenizer, and hardware bridges.
- **API Stabilization**: Ensure clean module exports and consistent type annotations across the Python API and CLI.

---

## Medio Termine (v2.x)
- **Format Expansion**: Add support for additional C64 container and disk formats such as `.g64`, `.t64`, `.prg` containers, and `.tap` tape images.
- **Performance Optimization**: Optimize BASIC tokenizer and detokenizer performance for large source files.
- **Enhanced Disk Tools**: Support directory sub-headers, BAM repair, and low-level sector inspection tools.

---

## Lungo Termine
- **Advanced CI/CD**: Full automated testing pipelines with cross-platform release management.
- **Hardware Bridges Expansion**: Integrate support for new hardware targets (e.g. Ultimate64 extended commands, TC64, MiSTer C64 core).
- **Auto-generated Documentation**: Generate comprehensive API documentation using Sphinx or MkDocs with live usage examples.
