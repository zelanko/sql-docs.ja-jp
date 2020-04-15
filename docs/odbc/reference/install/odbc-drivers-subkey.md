---
title: ODBC ドライバ サブキー |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304033"
---
# <a name="odbc-drivers-subkey"></a>ODBC ドライバーのサブキー
ODBC ドライバ サブキーの下の値には、インストールされているドライバが一覧表示されます。 これらの値の形式を次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|*ドライバーの説明*|REG_SZ|**インストール済み**|  
  
 *ドライバの説明*名は、ドライバ開発者によって定義されます。 通常、ドライバに関連付けられている DBMS の名前です。  
  
 たとえば、フォーマットされたテキスト ファイルと SQL Server 用のドライバーがインストールされているとします。 ODBC ドライバ サブキーの下の値は次のようになります。  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
