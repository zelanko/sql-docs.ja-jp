---
title: "SQLBulkOperations とブックマークによる行の更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], updating rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c626472dd121d39ae01ac90824a7977587401944
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>SQLBulkOperations とブックマークによる行の更新
ブックマークで行を更新するときに**SQLBulkOperations**ようにデータ ソース テーブルの 1 つまたは複数の行を更新します。 行は、バインドされたブックマーク列内のブックマークで識別されます。 アプリケーションのバッファーで列の長さ/インジケーター バッファー内の値がの場合を除き SQL_COLUMN_IGNORE) バインドされた各列のデータを使用して、行が更新されます。 バインドされていない列は更新されません。  
  
 持つブックマークで行を更新する**SQLBulkOperations**アプリケーション。  
  
1.  取得し、更新するすべての行のブックマークをキャッシュします。 複数のブックマークが存在し、列方向のバインドを使用した場合、それらのブックマークは配列であるに保存します。複数のブックマークが存在し、行方向のバインドを使用した場合、それらのブックマークは、行の構造体の配列に格納されます。  
  
2.  ブックマークの数を SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を設定し、ブックマークの値、または列 0 へのブックマークの配列を含むバッファーをバインドします。  
  
3.  行セットのバッファーで新しいデータ値を配置します。 長い形式のデータを送信する方法について**SQLBulkOperations**を参照してください[長い形式のデータおよび SQLSetPos SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)です。  
  
4.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、バイナリのバッファー、および SQL_NULL_DATA を NULL に設定する列にバインドされた列のデータのバイト長文字列バッファーにバインドされている列のデータまたは SQL_NTS のバイト長です。  
  
5.  SQL_COLUMN_IGNORE に更新されますが、これらの列の長さ/インジケーター バッファーの値を設定します。 アプリケーションは、この手順をスキップし、既存のデータを再送信、この効率的ではありませんし、リスクが切り詰められました。 読み取られたときにデータ ソースに値を送信します。  
  
6.  呼び出し**SQLBulkOperations**で、*操作*引数 SQL_UPDATE_BY_BOOKMARK に設定します。  
  
 更新プログラムとしてデータ ソースに送信されるすべての行でアプリケーション バッファーは有効な行データである必要があります。 アプリケーション バッファーがいっぱいになった場合、フェッチによって行の状態配列が維持されている場合、および行の状態値が SQL_ROW_DELETED、SQL_ROW_ERROR、または SQL_ROW_NOROW である場合は、無効なデータは、データ ソースに誤って送信でした。
