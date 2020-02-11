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
ms.openlocfilehash: eb54ba7becad42d8d9d2c2870c02db37a3c7d89f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093982"
---
# <a name="odbc-drivers-subkey"></a>ODBC ドライバーのサブキー
[ODBC ドライバー] サブキーの下の値には、インストールされているドライバーが一覧表示されます。 これらの値の形式を次の表に示します。  
  
|Name|データ型|データ|  
|----------|---------------|----------|  
|*ドライバー-説明*|REG_SZ|**ら**|  
  
 *ドライバーの説明*名は、ドライバーの開発者によって定義されます。 通常は、ドライバーに関連付けられている DBMS の名前です。  
  
 たとえば、フォーマットされたテキストファイルと SQL Server にドライバーがインストールされているとします。 ODBC ドライバーサブキーの下の値は次のようになります。  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
