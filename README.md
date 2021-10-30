# Disk Partition Info

Disk Partition Info is a C#/.NET class library that allows you to read various low-level physical disk information such as the [Master Boot Record (MBR)](https://en.wikipedia.org/wiki/Master_boot_record), [GUID Partition Table (GPT)](https://en.wikipedia.org/wiki/GUID_Partition_Table) and different filesystem headers like [NTFS](https://en.wikipedia.org/wiki/NTFS), [FAT32](https://en.wikipedia.org/wiki/File_Allocation_Table), [exFAT](https://en.wikipedia.org/wiki/ExFAT), [ext2](https://en.wikipedia.org/wiki/Ext2)/[ext3](https://en.wikipedia.org/wiki/Ext3)/[ext4](https://en.wikipedia.org/wiki/Ext4), etc.

It _should_ work on both Windows, Linux and macOS although only Windows was tested.

## Build

* Install [.NET 5 SDK](https://dotnet.microsoft.com/download/dotnet/5.0) on your system
* Run `dotnet build`

## Usage

### Master Boot Record (MBR)

```csharp
var mbr = DiskPartitionInfo.ReadMbr()
    .FromPath("disk.img");
    // or .FromStream(memoryStream);
    // or .FromPhysicalDriveNumber(0); (Windows only)
    // or .FromVolumeLetter("C:");     (Windows only)
```

### GUID Partition Table (GPT)

```csharp
var gpt = DiskPartitionInfo.ReadGpt()
    .Primary()
    // or .Secondary()
    .FromPath("disk.img");
    // or .FromStream(memoryStream);
    // or .FromPhysicalDriveNumber(0); (Windows only)
    // or .FromVolumeLetter("C:");     (Windows only)
```

### Filesystem headers

Not implemented yet
