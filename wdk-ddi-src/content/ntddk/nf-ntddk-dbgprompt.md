---
UID: NF:ntddk.DbgPrompt
title: DbgPrompt function (ntddk.h)
description: The DbgPrompt routine displays a caller-specified user prompt string on the kernel debugger's display device and obtains a user response string.
old-location: devtest\dbgprompt.htm
tech.root: devtest
ms.date: 02/23/2018
keywords: ["DbgPrompt function"]
ms.keywords: DbgPrompt, DbgPrompt routine [Driver Development Tools], DebugFns_bf0bb6f5-3664-4f8d-811e-5d55fbb94081.xml, devtest.dbgprompt, ntddk/DbgPrompt
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtDll.lib (user mode); NtosKrnl.lib (kernel mode)
req.dll: NtDll.dll (user mode); NtosKrnl.exe (kernel mode)
req.irql: <= DIRQL
targetos: Windows
req.typenames: 
f1_keywords:
 - DbgPrompt
 - ntddk/DbgPrompt
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - NtDll.dll
 - NtosKrnl.exe
api_name:
 - DbgPrompt
---

# DbgPrompt function


## -description

The <b>DbgPrompt</b> routine displays a caller-specified user prompt string on the kernel debugger's display device and obtains a user response string.

## -parameters

### -param Prompt [in]


A pointer to a NULL-terminated constant character string that the debugger will display as a user prompt. The maximum size of this string is 512 characters.

### -param Response [out]


A pointer to a character array buffer that receives the user's response, including a terminating newline character. The maximum size of this buffer is 512 characters.

### -param Length

<p>The size, in characters, of the buffer that receives the user's response. This size is the maximum number of characters that the routine will return.</p>

## -returns

<b>DbgPrompt</b> returns the number of characters that the <i>Response</i> buffer received, including the terminating newline character. <b>DbgPrompt</b> returns zero if it receives no characters.

## -remarks

The <b>DbgPrompt</b> routine displays the specified prompt string on the kernel debugger's display device and then reads a line of user input text. 

After <b>DbgPrompt</b> returns, the <i>Response</i> buffer contains the user's response, including the terminating newline character. The user response string is not NULL-terminated.

The following code example asks if the user wants to continue and accepts the letter "y" for yes and the letter "n" for no.


```
CHAR Response[2];
BOOLEAN Continue = FALSE;
ULONG CharCount;
for (;;) {
 CharCount = DbgPrompt(
  "Do you want to continue? (Type y or n, then type Enter.) ",
  Response,
  sizeof(Response)
  );

 if (CharCount == 2) {
 if (Response[0] == 'y') {
  Continue = TRUE;
  break;
  } else if (Response[0] == 'n') {
  break;
     }
    }

    //
    // Incorrect response. Display the prompt again.
    //
}
 
```


