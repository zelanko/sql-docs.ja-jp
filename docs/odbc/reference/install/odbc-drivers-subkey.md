---
title: "ODBC ドライバーのサブキー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 756f1f145d7e9a8ea5698366af920cce13041dd2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-drivers-subkey"></a>ODBC ドライバーのサブキー
ODBC ドライバーのサブキーの下の値では、インストールされたドライバーが一覧表示します。 これらの値の形式は次の表に示します。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|*ドライバーの説明*|REG_SZ|**インストールされています。**|  
  
 *ドライバー説明*名は、ドライバーの開発者によって定義されます。 通常、ドライバーに関連付けられている DBMS の名前です。  
  
 たとえば、書式設定されたテキスト ファイルと SQL Server のドライバーがインストールされているとします。 ODBC ドライバーのサブキーの下の値があります。  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
