# fv-win-vmod

## Code flow of test_auto_patching

1. Parse arguments of terminal
2. Load database (patch.dat, vmod-vuln-oft.dat) and get valid signatures
3. Running correspond method 
    1. Download
        1. Check download type
            - Type 3:
                - Call patchInfoJson
    2. Install
    3. Check feed