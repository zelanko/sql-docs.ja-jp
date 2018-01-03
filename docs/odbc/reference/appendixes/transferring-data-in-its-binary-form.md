---
title: "データ転送のバイナリ形式の |Microsoft ドキュメント"
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
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7241124d7297dd661c3aef08701af0cc15d77d1e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="transferring-data-in-its-binary-form"></a>バイナリ形式のデータを転送します。
アプリケーションは、同じ DBMS およびハードウェア プラットフォームを使用する 2 つのデータ ソース間 (内部形式で指定した DBMS によって使用される) のデータを安全に転送できます。 特定の部分のデータは、SQL データ型はソースとターゲットのデータ ソースで同じである必要があります。 C データ型は、SQL_C_BINARY です。  
  
 アプリケーションを呼び出すと**SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**ソースのデータ ソースからデータを取得、ドライバーでは、データからのデータを取得ソースし、型の SQL_C_BINARY の記憶域の場所への変換なしに転送します。 アプリケーションを呼び出すと**SQLBulkOperations**、 **SQLExecute**、 **SQLExecDirect**、 **SQLPutData、または SQLSetPos**データを送信するには対象のデータ ソース、ドライバーは、記憶域の場所からデータを取得し、ターゲット データ ソースへの変換を行わずを転送します。  
  
> [!NOTE]  
>  この方法で (バイナリ データ) を除くすべてのデータを転送するアプリケーションは、Dbms の間で相互運用可能ではありません。  
  
 **SQLCopyDesc**マップ元 DBMS から目的の DBMS でのパラメーター バインドに行のバインドをコピーするために使用できます。
