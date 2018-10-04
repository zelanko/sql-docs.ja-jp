---
title: バイナリ形式でデータを転送する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44bf8de8ea4c33a20a6159c5702db0b7eaee9eed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626630"
---
# <a name="transferring-data-in-its-binary-form"></a>バイナリ形式でのデータ転送
アプリケーションは、同じ DBMS およびハードウェア プラットフォームを使用して、2 つのデータ ソース間で (指定した DBMS で使用される内部形式) でのデータを安全に転送できます。 所定のデータでは、、SQL データ型は、ソースとターゲットのデータ ソースに同じ数である必要があります。 C データ型は、SQL_C_BINARY です。  
  
 アプリケーションを呼び出すと**SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**ドライバーが、データからデータを取得、ソースのデータ ソースからデータを取得するにはソースし、型の SQL_C_BINARY の記憶域の場所、変換せずに転送します。 アプリケーションを呼び出すと**SQLBulkOperations**、 **SQLExecute**、 **SQLExecDirect**、 **SQLPutData、または SQLSetPos**データを送信するには対象のデータ ソース、ドライバーは、記憶域の場所からデータを取得し、ターゲット データ ソースへの変換せずに転送します。  
  
> [!NOTE]  
>  この方法で (バイナリ データ) を除くすべてのデータを転送するアプリケーションは、Dbms の間で相互運用可能ではありません。  
  
 **SQLCopyDesc**ターゲット DBMS でのパラメーター バインドに、マップ元 DBMS の行バインドのコピーを使用できます。
