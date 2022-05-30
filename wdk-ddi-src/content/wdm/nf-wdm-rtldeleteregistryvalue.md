---
UID: NF:wdm.RtlDeleteRegistryValue
title: RtlDeleteRegistryValue function (wdm.h)
description: The RtlDeleteRegistryValue routine removes the specified entry name and the associated values from the registry along the given relative path.
old-location: kernel\rtldeleteregistryvalue.htm
tech.root: kernel
ms.date: 04/30/2018
keywords: ["RtlDeleteRegistryValue function"]
ms.keywords: RtlDeleteRegistryValue, RtlDeleteRegistryValue routine [Kernel-Mode Driver Architecture], k109_ad2e98c7-7787-49b2-b2af-1782d7f64e0d.xml, kernel.rtldeleteregistryvalue, wdm/RtlDeleteRegistryValue
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: IrqlRtlPassive, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
targetos: Windows
req.typenames: 
f1_keywords:
 - RtlDeleteRegistryValue
 - wdm/RtlDeleteRegistryValue
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - NtosKrnl.exe
api_name:
 - RtlDeleteRegistryValue
---

# RtlDeleteRegistryValue function


## -description

The <b>RtlDeleteRegistryValue</b> routine removes the specified entry name and the associated values from the registry along the given relative path.

## -parameters

### -param RelativeTo [in]


Specifies whether <i>Path</i> is an absolute registry path or is relative to a predefined key path as one of the following.

<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>
RTL_REGISTRY_ABSOLUTE

</td>
<td>
Path is an absolute registry path.

</td>
</tr>
<tr>
<td>
RTL_REGISTRY_SERVICES

</td>
<td>
Path is relative to <b>\Registry\Machine\System\CurrentControlSet\Services</b>.

</td>
</tr>
<tr>
<td>
RTL_REGISTRY_CONTROL

</td>
<td>
Path is relative to <b>\Registry\Machine\System\CurrentControlSet\Control</b>.

</td>
</tr>
<tr>
<td>
RTL_REGISTRY_WINDOWS_NT

</td>
<td>
Path is relative to <b>\Registry\Machine\Software\Microsoft\Windows NT\CurrentVersion</b>.

</td>
</tr>
<tr>
<td>
RTL_REGISTRY_DEVICEMAP

</td>
<td>
Path is relative to <b>\Registry\Machine\Hardware\DeviceMap</b>.

</td>
</tr>
<tr>
<td>
RTL_REGISTRY_USER

</td>
<td>
Path is relative to <b>\Registry\User\CurrentUser</b>. (For a system process, this is <b>\Users\.Default</b>.)

</td>
</tr>
<tr>
<td>
RTL_REGISTRY_HANDLE

</td>
<td>
Specifies that the <i>Path</i> parameter is actually a registry handle to use. This value is optional.

</td>
</tr>
</table>

### -param Path [in]


Specifies the registry path according to the <i>RelativeTo</i> value. If RTL_REGISTRY_HANDLE is set, <i>Path</i> is a handle to be used directly.

### -param ValueName [in]


Pointer to the value name to be removed from the registry.

## -returns

<b>RtlDeleteRegistryValue</b> returns STATUS_SUCCESS if the value entry was deleted.

Note that if <i>RelativeTo</i> is set to RTL_REGISTRY_HANDLE, the following occurs:

<ul>
<li>
On Windows 98/Me, Windows NT 4.0 and 2000, the routine closes the specified handle before returning.

</li>
<li>
On Windows XP and later versions of Windows, the routine leaves the handle open.

</li>
</ul>

## -see-also

<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-rtlcheckregistrykey">RtlCheckRegistryKey</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-rtlqueryregistryvalues">RtlQueryRegistryValues</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-rtlwriteregistryvalue">RtlWriteRegistryValue</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-zwenumeratekey">ZwEnumerateKey</a>



<a href="/windows-hardware/drivers/ddi/wdm/nf-wdm-zwopenkey">ZwOpenKey</a>
