---
UID: NS:dbgmodel.SymbolSearchInfo
title: SymbolSearchInfo
author: windows-driver-content
description: 
ms.assetid: ebc50d46-6c19-436b-a0bb-eb1e2da38f7b
ms.author: windowsdriverdev
ms.date: 07/16/2018
ms.topic: struct
ms.prod: windows-hardware
ms.technology: windows-devices
ms.keywords: SymbolSearchInfo, , 
req.header: dbgmodel.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.ddi-compliance:
req.unicode-ansi:
req.max-support:
req.typenames: 
topic_type: 
-	apiref
api_type: 
-	HeaderDef
api_location: 
-	dbgmodel.h
api_name: 
-	SymbolSearchInfo
product: Windows
targetos: Windows
---

# SymbolSearchInfo structure

## -description

The search record passed to EnumerateChildrenEx in order to restrict symbol searches.

A given kind of symbol (as indicated by the SymbolKind enumeration) searched may have its own derived type.

## -struct-fields

### -field HeaderSize

sizeof(SymbolSearchInfo)

  
### -field InfoSize
sizeof(* by SymbolKind *)

 
### -field SearchOptions

What follows is per SymbolKind.
   

## -remarks

## -see-also

[Debugger Data Model C++ Overview](https://review.docs.microsoft.com/en-us/windows-hardware/drivers/debugger/data-model-cpp-overview?branch=debugger-op-ref-docs)