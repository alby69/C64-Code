# C64-Code (readycode_py)

Python port of **READYCode** — a C64 BASIC V2 tokenizer, .d64/.d81 disk image editor, and hardware bridge library.

Forked from [jbramwell/READYCode](https://github.com/jbramwell/READYCode) (Moonspace Labs, LLC), originally written in C#/.NET.

## Features

- **Tokenizer & PRG Converter**: Tokenize/detokenize C64 BASIC V2 source to/from real .prg binary format, with keyboard abbreviation support.
- **Disk Image Editor**: Parse and edit .d64 (1541) and .d81 (1581) disk images — BAM management, file CRUD, directory chain handling.
- **Minify / Prettify**: Reduce BASIC source size or improve readability.
- **Hardware Bridges**:
  - C64 Ultimate REST API (load/run PRG, machine control, disk mount/eject)
  - C64 Ultimate FTP client (browse storage)
  - VICE binary monitor (TCP, load/run/reset)
- **PETSCII**: PETSCII to C64 screen code conversion.

## Install

```bash
pip install readycode-py
```

Or from source:

```bash
git clone https://github.com/alby69/C64-Code.git
cd C64-Code
pip install -e ".[test]"
```

## Roadmap

See [docs/ROADMAP.md](docs/ROADMAP.md) for the project roadmap, future vision, and planned features.

## CLI Usage

```bash
# Tokenize BASIC → .prg
readycode tokenize input.bas -o output.prg

# Detokenize .prg → BASIC
readycode detokenize input.prg -o output.bas

# Disk image operations
readycode disk list mydisk.d64
readycode disk inject mydisk.d64 program.prg
readycode disk extract mydisk.d64 PROGRAM -o extracted.prg
readycode disk create -o newdisk.d64 --name "MY DISK"

# Minify / Prettify
readycode minify input.bas -o compact.bas
readycode prettify input.bas -o formatted.bas

# PETSCII conversion
readycode petscii $41

# Hardware bridges
readycode bridge-c64u run --host 192.168.1.100 --file program.prg
readycode bridge-vice run --file program.prg
```

## Python API

```python
from readycode_py.tokenizer import PrgConverter, BasicTokenizer
from readycode_py.diskimage import DiskImage, DiskGeometry, C64UFileKind
from readycode_py.transform import CodeMinifier, CodePrettifier
from readycode_py.vice_client import ViceClient
from readycode_py.ultimate_client import C64UltimateClient
from readycode_py.petscii import to_screen_code

# Tokenize
converter = PrgConverter()
prg_bytes = converter.convert_to_prg('10 PRINT "HELLO"\n20 GOTO 10')

# Detokenize
basic_text = converter.convert_from_prg(prg_bytes)

# Disk image
img = DiskImage(DiskGeometry.D64)
data = open("mydisk.d64", "rb").read()
entries = img.read_directory(data)
for e in entries:
    print(f"{e.name} ({len(e.content)} bytes)")
```

## Tests

```bash
pip install -e ".[test]"
pytest tests/ -v
```

## Credits

- **Original**: [READYCode](https://github.com/jbramwell/READYCode) by Moonspace Labs, LLC — MIT License
- **Python Port**: Alberto Abate — GPLv3 (within C64-Intelligence-SDK)

## License

GNU General Public License v3.0
