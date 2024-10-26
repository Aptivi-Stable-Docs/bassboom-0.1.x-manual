---
description: Formatting tools for your music files
---

# 📼 Format

Formatting tools for your music files in the Basolia library allow you to get information about your music file, such as getting a total duration, getting frame size and length, and getting ID3v2 metadata.

## Audio information tools

The formatting tools include the audio information tools, which allows you to get information about a music file that you've opened using the `OpenFile()` function.

### Getting a duration

You can get a duration of the whole music file using either the samples count or the time span using one of the below functions:

```csharp
// Total samples count
public static int GetDuration(bool scan)

// Time span
public static TimeSpan GetDurationSpan(bool scan)
```

Additionally, if you have a number of samples, such as what `GetDuration()` returned, you can use one of the following functions:

```csharp
// Format info is not known
public static TimeSpan GetDurationSpanFromSamples(int samples)

// Format info is known
public static TimeSpan GetDurationSpanFromSamples(int samples, (long rate, int channels, int encoding) formatInfo)
```

### Frame size and length

If you want to know the frame size of your music file and its length, you can use the two functions below:

```csharp
// Frame size
public static int GetFrameSize()

// Frame length
public static int GetFrameLength()
```

### Samples per frame

If you want to know the number of MPEG samples per single frame, you can use the below function:

```csharp
public static int GetSamplesPerFrame()
```

### Getting buffer size

To get the buffer size for your music file, you'll have to call the `GetBufferSize()` function.

```csharp
public static int GetBufferSize()
```

### ID3v2, ID3v1, and ICY metadata

To gather the ID3v2, ID3v1, and ICY metadata, the two functions provide you information about the music file:

```csharp
public static void GetId3Metadata(out Id3V1Metadata managedV1, out Id3V2Metadata managedV2)
public static string GetIcyMetadata()
```

The ID3v2 metadata contains the following information:

* `Title`: Song title
* `Artist`: Song artist
* `Album`: Song album
* `Year`: Song year
* `Comment`: Song comment
* `Genre`: Song genre
* `Comments`: A list of comments
* `Texts`: A list of extra text
* `Extras`: A list of extras
* `Pictures`: A list of pictures

The ID3v1 metadata contains the following information:

* `Tag`: Song tag
* `Title`: Song title
* `Artist`: Song artist
* `Album`: Song album
* `Year`: Song year
* `Comment`: Song comment
* `Genre`: Song genre. You can get its index using the `GenreIndex` property.

### Frame information

To get the complete frame information about your music file, you need to call the `GetFrameInfo()` function:

```csharp
public static FrameInfo GetFrameInfo()
```

A single `FrameInfo` instance returned by the above function contains the following information:

* `Version`: MPEG version
* `Layer`: Layer 1, 2, or 3
* `Rate`: Bitrate
* `Mode`: MPEG mode. You can get extended info using the ModeExt property.
* `FrameSize`: MPEG frame size
* `Flags`: Flags to indicate the originality of the song
* `Emphasis`: The song emphasis
* `BitRate`: Actual bitrate
* `AbrRate`: Average bitrate
* `Vbr`: Variable bitrate mode

## Format tools

In addition to the audio information tools, this library also ships the formatting tools that allow you to get format info for a song.

### Getting format info

To get format information for a song, you can use the GetFormatInfo() function that allows you to get a bit rate, number of channels, and the encoding used in a song:

```csharp
public static (long rate, int channels, int encoding) GetFormatInfo()
```

### Getting list of supported formats

In addition to getting a single format information, you can also get a list of supported formats that are supported by the sound device. This can be achieved by calling the `GetFormats()` function:

```csharp
public static FormatInfo[] GetFormats()
```

A single `FormatInfo` instance contains three properties:

* `Rate`: A bit rate
* `Channels`: Number of channels in a song file
* `Encoding`: Song encoding

## Decode tools

In order for BassBoom to play songs, they must be decoded before the resulting audio data can be sent to the target device. BassBoom's Basolia offers decoding tools.

### Manually decoding a frame

To manually decode a frame, you must use the `DecodeFrame()` function. Most of the time, you don't need to call it; BassBoom's Basolia will automatically call it for you when playback is commenced.

```csharp
public static int DecodeFrame(ref int num, ref byte[] audio, ref int bytes)
```

### Get/Set current decoder

If you want to get the current decoder or if you want to set the current decoder to something else, you need to use the `Decoder` property.

```csharp
public static string Decoder
```

{% hint style="info" %}
Make sure that you're using a decoder that's supported for your device. Otherwise, you'll get an error saying that the required decoder is not supported.
{% endhint %}

### Get current decoders

If you want to either get all the decoders that are implemented in the distributed version of MPG123 library, or if you want to get all the decoders that your system can use, you'll need to use the `GetDecoders` function.

```csharp
public static string[] GetDecoders(bool onlySupported)
```
