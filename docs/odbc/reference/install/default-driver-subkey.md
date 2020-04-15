---
title: 既定のドライバ サブキー |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb134d670964e352d94c13474d8a72fa4bd494ba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301055"
---
# <a name="default-driver-subkey"></a>既定のドライバーのサブキー
Default サブキーには、既定のデータ ソースで使用されるドライバーを記述する単一の値が含まれています。 この値の形式を次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|**Driver**|REG_SZ|*既定のドライバーの説明*|  
  
 *既定のドライバーの説明*名は、ドライバーを説明する ODBC ドライバー サブキーの値の名前と同じです。  
  
 たとえば、既定のデータ ソースが SQL Server ドライバを使用している場合、Default サブキーの下の値は次のようになります。  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  既定のサブキーに含まれる既定のドライバーは、既定のユーザー DSN または既定のシステム DSN のいずれかを参照できます。 デフォルトのユーザー DSN とデフォルトのシステム DSN の両方が作成されている場合、デフォルトのドライバーは最後に作成された DSN によって判別されるため、最初に作成された DSN の有効なエントリではない可能性があります。
