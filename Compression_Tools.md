# Linux Compression Tools

## Introduction

Compression tools in Linux help reduce file sizes for efficient storage and transfer. Different tools offer varying levels of compression speed and efficiency. Below are some commonly used compression utilities along with their commands.



### 1. **gzip**

- Compresses files using the `.gz` format.
- Command:
    
    ```bash
    gzip filename
    
    ```
    
- Decompress:
    
    ```bash
    gunzip filename.gz
    
    ```
    

### 2. **bzip2**

- Compresses files using the `.bz2` format (better compression than gzip but slower).
- Command:
    
    ```bash
    bzip2 filename
    
    ```
    
- Decompress:
    
    ```bash
    bunzip2 filename.bz2
    
    ```
    

### 3. **xz**

- Compresses files using the `.xz` format (high compression ratio, slower speed).
- Command:
    
    ```bash
    xz filename
    
    ```
    
- Decompress:
    
    ```bash
    unxz filename.xz
    
    ```
    

### 4. **zip**

- Creates a compressed archive in `.zip` format (supports multiple files).
- Command:
    
    ```bash
    zip archive.zip file1 file2
    
    ```
    
- Decompress:
    
    ```bash
    unzip archive.zip
    
    ```
    

### 5. **tar**

- Used to archive multiple files into one, optionally with compression (e.g., `.tar.gz`).
- Create a compressed tarball:
    
    ```bash
    tar -czvf archive.tar.gz file1 file2
    
    ```
    
- Decompress:
    
    ```bash
    tar -xzvf archive.tar.gz
    
    ```
    

### 6. **7z (p7zip)**

- High compression ratio using `.7z` format.
- Command:
    
    ```bash
    7z a archive.7z file1 file2
    
    ```
    
- Decompress:
    
    ```bash
    7z x archive.7z
    
    ```
    

### 7. **zstd**

- Fast compression with `.zst` format.
- Command:
    
    ```bash
    zstd filename
    
    ```
    
- Decompress:
    
    ```bash
    zstd -d filename.zst
    
    ```
    

These tools offer various options for balancing speed and compression ratio based on the use case.
