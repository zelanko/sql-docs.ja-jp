---
title: "ODBC ドライバーのサブキー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
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
ms.openlocfilehash: 171692642f04cbab5b1e289efdae89ab79f15831
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-drivers-subkey"></a>ODBC ドライバーのサブキー
ODBC ドライバーのサブキーの下の値では、インストールされたドライバーが一覧表示します。 これらの値の形式は次の表に示します。  
  
|[オブジェクト名]|データ型|data|  
|----------|---------------|----------|  
|*ドライバーの説明*|REG_SZ|**インストールされています。**|  
  
 *ドライバー説明*名は、ドライバーの開発者によって定義されます。 通常、ドライバーに関連付けられている DBMS の名前です。  
  
 たとえば、書式設定されたテキスト ファイルと SQL Server のドライバーがインストールされているとします。 ODBC ドライバーのサブキーの下の値があります。  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
