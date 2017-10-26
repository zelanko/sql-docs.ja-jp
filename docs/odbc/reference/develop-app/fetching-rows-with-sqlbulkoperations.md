---
title: "SQLBulkOperations を持つ行をフェッチ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f0e3f46b5dd742ff1e77c87a8486038c41839764
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="fetching-rows-with-sqlbulkoperations"></a>SQLBulkOperations を持つ行のフェッチ
呼び出しによってブックマークを使用して行セットにデータを再フェッチ**SQLBulkOperations です。** フェッチする行は、バインドされたブックマーク列内のブックマークで識別されます。 SQL_COLUMN_IGNORE の値を持つ列はフェッチされません。  
  
 一括フェッチを実行する**SQLBulkOperations**アプリケーションは、次を実行します。  
  
1.  取得し、更新するすべての行のブックマークをキャッシュします。 複数のブックマークが存在し、列方向のバインドを使用した場合、それらのブックマークは配列であるに保存します。複数のブックマークが存在し、行方向のバインドを使用した場合、それらのブックマークは、行の構造体の配列に格納されます。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性をフェッチする行の数に設定し、ブックマークの値、または列 0 へのブックマークの配列を含むバッファーをバインドします。  
  
3.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、バイナリのバッファー、および SQL_NULL_DATA を NULL に設定する列にバインドされた列のデータのバイト長文字列バッファーにバインドされている列のデータまたは SQL_NTS のバイト長です。 アプリケーションは、(存在する場合、既定値に設定するのには、これらの列または SQL_COLUMN_IGNORE を NULL (1 つでない場合) の長さ/インジケーター バッファーの値を設定します。  
  
4.  呼び出し**SQLBulkOperations**で、*操作*引数 SQL_FETCH_BY_BOOKMARK に設定します。  
  
 特定の列上で実行される操作を防ぐために、行操作配列を使用するアプリケーションの必要はありません。 アプリケーションでは、バインドされたブックマーク配列にこれらの行のブックマークのみをコピーすることによってフェッチする行を選択します。

