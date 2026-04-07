# Metadata-file-checking

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

example: /media/sf_image/image/

## 1️⃣ Begin file Checking

Get inside the folder first

```bash
cd /media/sf_image/image
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

<img width="595" height="72" alt="image" src="https://github.com/user-attachments/assets/9f291b81-984a-41da-acf4-68364d84766b" />
