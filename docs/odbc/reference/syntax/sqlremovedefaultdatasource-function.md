---
title: 関数を削除する |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 952ace7d17e8bb5b4c824761b02e5c8a0895f519
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303943"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource 関数
**適合 性**  
 バージョン導入: ODBC 1.0、非推奨  
  
 **まとめ**  
 ODBC 3.0 では **、関数は***、ODBC_REMOVE_DEFAULT_DSNの fRequest*引数を持つ[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)の呼び出しに置き換えられました。 ODBC 2 *.x*インストール プログラムがこの関数を呼び出す場合、ODBC インストーラーは、次の**SQLConfigDataSource**呼び出しにマップします。  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
