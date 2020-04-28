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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd1f8d3293e35a543cce6b5079d9c6e10a331a88
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304033"
---
# <a name="odbc-drivers-subkey"></a>ODBC ドライバーのサブキー
[ODBC ドライバー] サブキーの下の値には、インストールされているドライバーが一覧表示されます。 これらの値の形式を次の表に示します。  
  
|名前|データの種類|データ|  
|----------|---------------|----------|  
|*ドライバー-説明*|REG_SZ|**インストール済み**|  
  
 *ドライバーの説明*名は、ドライバーの開発者によって定義されます。 通常は、ドライバーに関連付けられている DBMS の名前です。  
  
 たとえば、フォーマットされたテキストファイルと SQL Server にドライバーがインストールされているとします。 ODBC ドライバーサブキーの下の値は次のようになります。  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
