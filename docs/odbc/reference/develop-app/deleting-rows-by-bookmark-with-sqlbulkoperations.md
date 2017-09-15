---
title: "SQLBulkOperations を持つブックマークによる行の削除 |Microsoft ドキュメント"
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
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: db7e04c5bf76855afdb24676c905c5cccbc60cbc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>SQLBulkOperations とブックマークによる行の削除
ブックマークで行を削除するときに**SQLBulkOperations**ようにデータ ソース テーブルの 1 つまたは複数の選択した行を削除します。 行は、バインドされたブックマーク列内のブックマークで識別されます。  
  
 持つブックマークによって行を削除する**SQLBulkOperations**アプリケーションは、次を実行します。  
  
1.  取得し、削除するすべての行のブックマークをキャッシュします。 複数のブックマークが存在し、列方向のバインドを使用した場合、それらのブックマークは配列であるに保存します。複数のブックマークが存在し、行方向のバインドを使用した場合、それらのブックマークは、行の構造体の配列に格納されます。  
  
2.  ブックマークの数を SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を設定し、ブックマークの値、または列 0 へのブックマークの配列を含むバッファーをバインドします。  
  
3.  呼び出し**SQLBulkOperations**で*操作*SQL_DELETE_BY_BOOKMARK に設定します。
