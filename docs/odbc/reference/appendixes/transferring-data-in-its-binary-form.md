---
title: バイナリ形式でのデータ転送 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 53531ff4a3b2e1441fabf22ec7a3ce12b15540eb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301414"
---
# <a name="transferring-data-in-its-binary-form"></a>バイナリ形式でのデータ転送
アプリケーションは、同じ DBMS とハードウェア プラットフォームを使用する 2 つのデータ ソース間で、(指定された DBMS で使用される内部形式で) 安全にデータを転送できます。 特定のデータについて、SQL データ型はソースとターゲットのデータ ソースで同じである必要があります。 C データ型がSQL_C_BINARY。  
  
 アプリケーションが SQLFetch 、 **SQLFetchScroll**、または**SQLFetchScroll****SQLGetData**を呼び出してソース データ ソースからデータを取得すると、ドライバーはデータ ソースからデータを取得し、変換せずにデータ ソースをSQL_C_BINARY型の格納場所に転送します。 アプリケーションが、ターゲット データ ソースにデータを送信する**SQLBulkOperations、SQLExecute、SQLExecDirect、SQLPutData、または SQLSetPos を**呼び出すと、ドライバーは、ストレージの場所からデータを取得し、変換せずにターゲット データ ソースに転送します。 **SQLBulkOperations** **SQLExecute** **SQLExecDirect**  
  
> [!NOTE]  
>  この方法でデータ (バイナリ データを除く) を転送するアプリケーションは、DBMS 間で相互運用できません。  
  
 **SQLCopyDesc**を使用して、ソース DBMS からターゲット DBMS のパラメータ バインディングに行バインディングをコピーできます。
