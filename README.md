# carma exceptions bug

Simply linking to the carma library seems to break pybind11's ability to handle exceptions. See `CMakeLists.txt`. Rather than throwing them to Python, the program crashes.

I only see this on Windows--the bug didn't appear when I built on WSL Ubuntu.

```bash
cmake -B build -S .
cmake --build
python pymod_test.py
```

System:
- Windows 10 Pro
- Clang 11
- pybind11 v2.7.1
- carma 0.6.1