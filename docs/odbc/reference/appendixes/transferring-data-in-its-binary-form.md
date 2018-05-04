---
title: データ転送のバイナリ形式の |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2d1227af9eeb303bc0d9bc56733e6bda9b5325c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="transferring-data-in-its-binary-form"></a>バイナリ形式のデータを転送します。
アプリケーションは、同じ DBMS およびハードウェア プラットフォームを使用する 2 つのデータ ソース間 (内部形式で指定した DBMS によって使用される) のデータを安全に転送できます。 特定の部分のデータは、SQL データ型はソースとターゲットのデータ ソースで同じである必要があります。 C データ型は、SQL_C_BINARY です。  
  
 アプリケーションを呼び出すと**SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**ソースのデータ ソースからデータを取得、ドライバーでは、データからのデータを取得ソースし、型の SQL_C_BINARY の記憶域の場所への変換なしに転送します。 アプリケーションを呼び出すと**SQLBulkOperations**、 **SQLExecute**、 **SQLExecDirect**、 **SQLPutData、または SQLSetPos**データを送信するには対象のデータ ソース、ドライバーは、記憶域の場所からデータを取得し、ターゲット データ ソースへの変換を行わずを転送します。  
  
> [!NOTE]  
>  この方法で (バイナリ データ) を除くすべてのデータを転送するアプリケーションは、Dbms の間で相互運用可能ではありません。  
  
 **SQLCopyDesc**マップ元 DBMS から目的の DBMS でのパラメーター バインドに行のバインドをコピーするために使用できます。
