---
title: SQLRemoveDefaultDataSource 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDefaultDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDefaultDataSource
helpviewer_keywords:
- SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea540d2ef6747bbe3bfc9ac55f04afe1d63349f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537242"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 では、非推奨とされます。  
  
 **まとめ**  
 ODBC 3.0 で、 **SQLRemoveDefaultDataSource**関数への呼び出しによって置き換えられました[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)で、*起こり*ODBC_REMOVE_DEFAULT_DSN の引数。 場合、ODBC 2 *.x*インストール プログラムは、この関数を呼び出し、ODBC のインストーラーを使用すると、次にマップする**SQLConfigDataSource**呼び出し。  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
