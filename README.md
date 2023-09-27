Grew tired of having to boot up Visual Studio every time I need a DLL, so this is a template written in Rust that can be compiled from both Linux and Windows, and export arbitrary functions for full flexibility.  

> Note: You will probably still need to run this on a windows VM for maximum ease-of-use. For `x86_64-pc-windows-msvc` builds you'll need the Visual Studio linker.

I could compile `x86_64-pc-windows-gnu` DLLs on Linux, as follows:

```bash
# You will likely need a cross-compiler:
sudo apt-get install mingw-w64

rustup target add x86_64-pc-windows-gnu
cargo build --target x86_64-pc-windows-gnu --release
```

You can test your payload's functionality using `rundll32.exe`:

```powershell
rundll32.exe .\target\release\shelldll.dll,some_export
```