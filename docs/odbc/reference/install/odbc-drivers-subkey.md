---
title: ODBC ドライバーのサブキー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 925e24f295602d7e66fe37935b53724b4d162adf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-drivers-subkey"></a>ODBC ドライバーのサブキー
ODBC ドライバーのサブキーの下の値では、インストールされたドライバーが一覧表示します。 これらの値の形式は次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|*ドライバーの説明*|REG_SZ|**インストールされています。**|  
  
 *ドライバー説明*名は、ドライバーの開発者によって定義されます。 通常、ドライバーに関連付けられている DBMS の名前です。  
  
 たとえば、書式設定されたテキスト ファイルと SQL Server のドライバーがインストールされているとします。 ODBC ドライバーのサブキーの下の値があります。  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
