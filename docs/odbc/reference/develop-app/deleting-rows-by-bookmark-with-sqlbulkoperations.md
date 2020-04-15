---
title: ブックマークによる行の削除操作 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b6a4c1b24ee276c86175392eb45ac5ce0aa45e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305963"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>SQLBulkOperations を使ったブックマークによる行の削除
ブックマークによって行を削除すると **、SQLBulkOperations によって**、テーブルの選択された行が 1 つ以上削除されます。 行は、バインドされたブックマーク列のブックマークによって識別されます。  
  
 **SQLBulkOperations**を使用してブックマークを使用して行を削除するには、アプリケーションは次の操作を行います。  
  
1.  削除するすべての行のブックマークを取得してキャッシュします。 複数のブックマークがあり、列方向のバインドが使用される場合、ブックマークは配列に格納されます。複数のブックマークがあり、行方向のバインドが使用されている場合、ブックマークは行構造の配列に格納されます。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性をブックマークの数に設定し、ブックマーク値またはブックマークの配列を含むバッファーを列 0 にバインドします。  
  
3.  SQL_DELETE_BY_BOOKMARK**に設定された操作で SQLBulkOperation**を呼び出します。 *Operation*
