---
title: 既定のドライバーサブキー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e82644d3bddab5d4f6fde6f7103bd9731872bab9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094196"
---
# <a name="default-driver-subkey"></a>既定のドライバーのサブキー
既定のサブキーには、既定のデータソースで使用されるドライバーを示す単一の値が含まれます。 この値の形式を次の表に示します。  
  
|Name|データ型|データ|  
|----------|---------------|----------|  
|**Driver**|REG_SZ|*既定のドライバー-説明*|  
  
 ドライバーの*説明の既定*の名前は、ドライバーを説明する ODBC ドライバーのサブキーの下の値の名前と同じです。  
  
 たとえば、既定のデータソースで SQL Server ドライバーが使用されている場合、既定のサブキーの下の値は次のようになります。  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  既定のサブキーに含まれている既定のドライバーは、既定のユーザー DSN または既定のシステム DSN を参照できます。 既定のユーザー DSN と既定のシステム DSN の両方が作成されている場合、既定のドライバーは最後に作成された DSN によって決定されるため、最初に作成された DSN の有効なエントリではない可能性があります。
