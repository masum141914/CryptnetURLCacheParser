# CryptnetURLCacheParser

# This is a Updated Version of mine MASUM BILLAH, we also add ELF file and EXE file (both Updated)

CryptnetURLCacheParser is a tool to parse CryptAPI cache files located on the following paths:

```
C:\Windows\System32\config\systemprofile\AppData\LocalLow\Microsoft\CryptnetUrlCache
C:\Windows\SysWOW64\config\systemprofile\AppData\LocalLow\Microsoft\CryptnetUrlCache
C:\Users\<USERNAME>\AppData\LocalLow\Microsoft\CryptnetUrlCache
```

The `metadata` folder contains metadata about the downloaded files. Each file contain the following data:

1. Timestamp : This is the last time the file was downloaded.
2. URL : The URL form where the file was downloaded.
3. FileSize : The downloaded file size in bytes.
4. MetadataHash : The hash for the downloaded file.  The following is some of the hashing algorithms absorved:
   * SHA1
   * SHA256
   * MD5
5. FullPath : The full path for the parsed file.
6. MD5 (Optional) : The calculated MD5 hash for the actual file in the `content` folder. This field is only available if you used the `--useConent` option.

## Installation

### From source

clone the repository:

```
git clone https://github.com/AbdulRhmanAlfaifi/CryptnetURLCacheParser
```

### Precompiled

You can use the latest compiled windows executable and ELF from here

## How to use

The following is the command line tool help message:

```
usage: CryptnetUrlCacheParser.py [-h] [-d DIRS [DIRS ...]] [-o OUTPUT]
                                 [--outputFormat {csv,json,jsonl}]
                                 [--useContent]

CryptnetUrlCache Metadata Parser - Developded by AbdulRhman Alfaifi

optional arguments:
  -h, --help            show this help message and exit
  -d DIRS [DIRS ...], --dirs DIRS [DIRS ...]
                        A list of dirs that contain certutil cache files
                        (default: all certutil cache paths)
  -o OUTPUT, --output OUTPUT
                        The file path to write the output to (default: stdout)
  --outputFormat {csv,json,jsonl}
                        The output formate (default: csv)
  --useContent          Try finding the cached file and calculate the MD5 hash
                        for it

Example::
python CryptonetURlCacheParser.py -d "C:\Users\Alice\AppData\LocalLow\Microsoft\CryptnetUrlCache\MetaData" -o "alice_cache.csv" --outputFormat csv --useContent

./CryptonetURlCacheParser -d /home/user/CryptnetCache/Metadata -o output.csv --outputFormat csv --useContent

CryptonetURlCacheParser.exe -d "C:\Users\Alice\AppData\LocalLow\Microsoft\CryptnetUrlCache\MetaData" -o output.csv --outputFormat csv --useContent
```

