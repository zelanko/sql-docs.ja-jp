---
title: SQLTransact マッピング |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304883"
---
# <a name="sqltransact-mapping"></a>SQLTransact のマッピング
**Sqltransact**は**SQLEndTran**に置き換えられました。 2つの関数の大きな違いは、 **SQLEndTran**には、実行する作業のスコープを指定する引数*handletype*が含まれていることです。 *Handletype*引数は、環境または接続ハンドルを指定できます。 **Sqltransact**の次の呼び出し:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 がにマップされています  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 *Connectionhandle*が SQL_NULL_HDBC と等しくない場合。 *Connectionhandle*引数は、 *hdbc*の値に設定されます。  
  
 **SQL_Transact**がにマップされています  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 *Connectionhandle*が SQL_NULL_HDBC と等しい場合は。 *EnvironmentHandle*引数は*henv*の値に設定されます。  
  
 どちらの場合も、*入力補完型*の引数は、 *fType*と同じ値に設定されます。
