---
ms.assetid: 62d77150-1d9e-4069-ab4a-299f33024912
title: Fsutil repair
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: "IT Pro"
ms.topic: article
ms.date: 10/16/2017
---
# Fsutil repair
> Applies to: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Administers and monitors NTFS self-healing repair operations.



## Syntax

```
fsutil repair [enumerate] <volumepath> [<LogName>]
fsutil repair [initiate] <VolumePath> <FileReference>
fsutil repair [query] <VolumePath>
fsutil repair [set] <VolumePath> <Flags>
fsutil repair [wait][<WaitType>] <VolumePath>

```

### Parameters

|Parameter|Description|
|-------------|---------------|
|enumerate|Enumerates the entires of a volume's corruption log.|
|\<volumepath>|Specifies the volume as the drive name followed by a colon.|
|\<LogName>|$Corrupt - The set of confirmed corruptions in the volume.<br />$Verify - A set of potential, unverified corruptions in the volume.|
|initiate|Initiates NTFS self-healing.|
|\<FileReference>|Specifies the NTFS volume-specific file ID (file reference number). The file reference includes the segment number of the file.|
|query|Queries the self-healing state of the NTFS volume.|
|set|Sets the self-healing state of the volume.|
|\<Flags>|Specifies the repair method to be used when setting the self-healing state of the volume.<p>The **Flags** parameter can be set to three values:<p>-   **0x01**: Enables general repair.<br />-   **0x09**: Warns about potential data loss without repair.<br />-   **0x00**: Disables NTFS self-healing repair operations.|
|state|Queries the corruption state of the system or for a given volume.|
|wait|Waits for repair(s) to complete. If NTFS has detected a problem on a volume on which it is performing repairs, this option allows the system to wait until the repair is complete before it runs any pending scripts.|
|[WaitType {0&#124;1}]|Indicates whether to wait for the current repair to complete or to wait for all repairs to complete. *WaitType* can be set to the following values:<p>-   **0**: Waits for all repairs to complete. (default value)<br />-   **1**: Waits for the current repair to complete.|

## Remarks

-   Self-healing NTFS attempts to correct corruptions of the NTFS file system online, without requiring **Chkdsk.exe** to be run. This feature was introduced in Windows Server 2008. For more information, see [Self Healing NTFS](https://go.microsoft.com/fwlink/?LinkID=165401).

## <a name="BKMK_examples"></a>Examples

To enumerate the confirmed corruptions of a volume, type:

```
fsutil repair enumerate C: $Corrupt 
```

To enable self-healing repair on drive C, type:

```
fsutil repair set c: 1
```

To disable self-healing repair on drive C, type:

```
fsutil repair set c: 0
```

## Additional References
- [Command-Line Syntax Key](command-line-syntax-key.md)

[Fsutil](Fsutil.md)

[Self Healing NTFS](https://go.microsoft.com/fwlink/?LinkID=165401)


