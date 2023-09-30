## CP Setup

Requirements:

1. Make sure compiler path is set up properly.

2. Install 'Code Runner' extension.

3. In settins.json add this shell script in code-runner.executorMap

    ```
    // [Remote Setup]

    "cpp": "if (-not (Test-Path './io')) { New-Item -Type Directory './io' } ; if (-not (Test-Path './io/input.txt')) { New-Item -Type File './io/input.txt' } ; if (-not (Test-Path './io/output.txt')) { New-Item -Type File './io/output.txt' } ; cd $dir && g++ -std=c++17 \"-Wl,--stack=268435456\" '$fileName' -o '$fileNameWithoutExt' && Get-Content './io/input.txt' | & $dir$fileNameWithoutExt.exe | Set-Content './io/output.txt' && del '$dir$fileNameWithoutExt.exe' && exit",
    ```
<br>
Now the main question, what deoes this shell do?

If you run a '.cpp' file it will create (if not already created)
 - io
   - input.txt
   - output.txt
 - random.cpp

**Input and Output will be redirected from and to these files.**



Credit: [Nadman Khan](https://github.com/NadmanKhan) wrote the shell script to redirect input and output.
I just added shell for creating input.txt and output.txt file for convinience.
Stack size part is added by [Mahir Shahriar](https://github.com/mahirshahriar1)

---
Final look:
![VS Code Setup - Final look](./VS%20Code%20Setup%20-%20Final%20look.png)
