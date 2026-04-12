# Metadata-file-checking

| File          | Tool      | Command / Link                                                                   | POC              | Analysis                                     |
| ------------- | --------- | -------------------------------------------------------------------------------- | ---------------- | -------------------------------------------- |
| Ocean.jpg     | exiftool  | [https://exif.tools/](https://exif.tools/)                                       | <img width="958" height="868" alt="image" src="https://github.com/user-attachments/assets/7a91e987-be97-4270-bf1a-fda34e2c6e11" /> | Online tools produce similar results as Kali |
|               |           | `exiftool ocean.jpg`                                                             | <img width="666" height="474" alt="image" src="https://github.com/user-attachments/assets/f8dda18a-4ce7-4e70-9850-6b05e001c742" /> | Flag found in metadata (comment section)     |
| Computer.jpg  | hexeditor | [https://hexed.it/](https://hexed.it/)                                           | <img width="1161" height="890" alt="image" src="https://github.com/user-attachments/assets/dac18685-6bed-4236-8d65-7381ab160557" /> | File header analysis can reveal hidden info  |
|               |           | `hexeditor computer.jpg`                                                         | <img width="651" height="478" alt="image" src="https://github.com/user-attachments/assets/f7ab5c18-03c1-49a1-a03b-abd036bc230a" /> | Easy to inspect binary structure             |
| dog.jpg       | binwalk   | `binwalk dog.jpg`<br>`binwalk -e dog.jpg`                                        | <img width="697" height="266" alt="image" src="https://github.com/user-attachments/assets/c0d4ed16-29fb-4d37-b93d-c5b5a23a2916" /> | Detects hidden/embedded files                |
|               |           | `cd _dog.jpg.extracted/`                                                         |                  | Extracted hidden content                     |
| Computer.jpg  | strings   | [https://www.dcode.fr/strings-extractor](https://www.dcode.fr/strings-extractor) | <img width="980" height="775" alt="image" src="https://github.com/user-attachments/assets/8213105a-27e7-4eeb-830d-1a23b5321377" /> | Online version of `strings`                  |
|               |           | `strings computer.jpg`                                                           | <img width="650" height="479" alt="image" src="https://github.com/user-attachments/assets/334bbf2e-aaa2-477f-8eef-04008a4cb5c8" /> | Extract readable text from binary            |
| solitaire.exe | file      | `file solitaire.exe`                                                             | <img width="631" height="71" alt="image" src="https://github.com/user-attachments/assets/358ac018-c804-42f2-a9ec-23824e9e00ef" /> | Actually identified as PNG file              |
| rubiks.jpg    | file      | `file rubiks.jpg`                                                                | <img width="595" height="72" alt="image" src="https://github.com/user-attachments/assets/9f291b81-984a-41da-acf4-68364d84766b" /> | File extension mismatch (PNG format)         |

____________________________________________________________________________________________________
## DETAILS STEP

## Share folder from windows

1. Choose a folder that want to be open in Kali Linux
2. Right click the folder and choose `Properties`
3. Click `Sharing` and choose `Advanced Sharing`
4. Tick `Share this folder`
5. Click `Permissions`
6. Tick `Allow` for **Full Control**, **Change** & **Read**
7. Click `Apply` and `OK`
8. Click `Apply` and `OK`
9. Click `Close`
10. Open **Kali Linux** in VirtualBox
11. Click `Devices` and then `Shared Folders` and `Shared Folders Settings...`
13. Click `Add new shared folder`, an icon with a folder and a plus sign
14. Choose the `Folder Path` and tick `Auto-mount`
15. Click `OK`

### Check the folder path

example: /media/sf_image/image/CD

## 1️⃣ Begin file Checking

Get inside the folder first

```bash
cd /media/sf_image
```

## 📂 2️⃣ Ocean.jpg → use EXIF (metadata)

**Command used**

```bash
exiftool ocean.jpg
```

**Result:**

<img width="748" height="558" alt="image" src="https://github.com/user-attachments/assets/ec24e2d9-32e8-4044-ba43-22c514c82ec6" />
<img width="742" height="439" alt="image" src="https://github.com/user-attachments/assets/13339308-72a7-498a-8e7d-2729265bcbc8" />

## 📂 3️⃣ Computer.jpg → use Hex Editor

1. Open link: https://hexed.it/
2. Click `Open file'
3. Choose the image (example: Computer.jpg)

**Result:**

<img width="1161" height="890" alt="image" src="https://github.com/user-attachments/assets/dac18685-6bed-4236-8d65-7381ab160557" />

## 📂 4️⃣ dog.jpg → use Binwalk

### 1. Check for hidden file

**Command used**

```bash
binwalk dog.jpg
```

**Result:**
<img width="697" height="266" alt="image" src="https://github.com/user-attachments/assets/c0d4ed16-29fb-4d37-b93d-c5b5a23a2916" />

### 2. Check for embedded file

**Command used**

```bash
binwalk -e dog.jpg
cd _dog.jpg.extracted/
ls /media/sf_image/image/_dog.jpg.extracted/hidden_text.txt
```
<img width="700" height="457" alt="image" src="https://github.com/user-attachments/assets/114f765f-ec3e-495d-90c9-143b9147cc90" />

## 📂 5️⃣ computer.jpg → use strings

1. Open link: https://www.dcode.fr/strings-extractor
2. CLick `INPUT FILE` and `Browse`
3. Choose the image (example: Computer.jpg)
4. Click `EXTRACT`

**Result:**

<img width="980" height="775" alt="image" src="https://github.com/user-attachments/assets/8213105a-27e7-4eeb-830d-1a23b5321377" />

## 📂 6️⃣ solitaire.exe → check file type

**Command used**

```bash
file solitaire.exe
```

**Result:**

<img width="631" height="71" alt="image" src="https://github.com/user-attachments/assets/358ac018-c804-42f2-a9ec-23824e9e00ef" />

## 📂 7️⃣ rubiks.jpg → check file

**Command used**

```bash
file rubiks.jpg
```

**Result:**

<img width="595" height="72" alt="image" src="https://github.com/user-attachments/assets/9f291b81-984a-41da-acf4-68364d84766b" />
