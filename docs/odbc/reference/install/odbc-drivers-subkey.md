---
title: ODBC ドライバーのサブキー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43be1c5e75998903ff4e64fc5f4230818a873ffc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63281130"
---
# <a name="odbc-drivers-subkey"></a>ODBC ドライバーのサブキー
ODBC ドライバーのサブキーの下の値には、インストールされているドライバーが一覧表示します。 これらの値の形式は、次の表に示します。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|*ドライバーの説明*|REG_SZ|**インストールされています。**|  
  
 *ドライバー説明*名は、ドライバーの開発者によって定義されます。 これは通常、ドライバーに関連付けられている DBMS の名前です。  
  
 たとえば、書式設定されたテキスト ファイルと SQL Server のドライバーがインストールされているとします。 ODBC ドライバーのサブキーの下の値は次のようになります。  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
