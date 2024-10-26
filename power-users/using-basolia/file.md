---
description: File management for BassBoom
icon: file-audio
---

# File

The file tools shipped with the BassBoom.Basolia library allows you to open and close a music file so that you can play music and get its information, such as the ID3v2 metadata information.

### Opening a music file

To be able to get the most out of the Basolia library, like playing MP3 files, you should call the `OpenFile()` function, pointing it to a path to a music file.

```csharp
public static void OpenFile(string path)
```

### Closing a music file

If you're done playing a music file or performing a specific operation on it, you can call the `CloseFile()` function to close the file.

```csharp
public static void CloseFile()
```
