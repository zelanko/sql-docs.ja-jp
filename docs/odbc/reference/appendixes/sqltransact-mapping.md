---
title: マッピングの実行 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6aaa056fca860a70f81ad7c3a4cd8539512bc25d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304883"
---
# <a name="sqltransact-mapping"></a>SQLTransact のマッピング
**SQLTransact**が**SQLEndTran**に置き換えられました。 2 つの関数の主な違いは **、SQLEndTran**に、実行する作業のスコープを指定する引数*HandleType*が含まれていることです。 *HandleType*引数は、環境または接続ハンドルを指定できます。 次の呼び出し**は、SQLTransact に**対して行われます。  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 にマップされています  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 *接続ハンドル*がSQL_NULL_HDBCと等しくない場合。 引数*は**、hdbc*の値に設定されます。  
  
 **SQL_Transact**がマップされている  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 *接続ハンドル*がSQL_NULL_HDBCに等しい場合。 引数*は* *henv*の値に設定されます。  
  
 上記の両方の場合 *、"完了タイプ"* 引数は*fType*と同じ値に設定されます。
