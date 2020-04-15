---
title: SQLBulk 操作を使用した行のフェッチ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae0b4c2114059cecaaf8f8825169300f131bd473
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305651"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>SQLBulkOperations による行のフェッチ
**SQLBulkOperations**の呼び出しによってブックマークを使用して、データを行セットに再フェッチできます。 フェッチされる行は、バインドされたブックマーク列のブックマークによって識別されます。 値がSQL_COLUMN_IGNOREの列はフェッチされません。  
  
 **SQLBulkOperations**を使用して一括フェッチを実行するには、アプリケーションは次の処理を実行します。  
  
1.  更新するすべての行のブックマークを取得してキャッシュします。 複数のブックマークがあり、列方向のバインドが使用される場合、ブックマークは配列に格納されます。複数のブックマークがあり、行方向のバインドが使用されている場合、ブックマークは行構造の配列に格納されます。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性をフェッチする行数に設定し、ブックマーク値またはブックマークの配列を含むバッファーを列 0 にバインドします。  
  
3.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、文字列バッファーにバインドされた列のデータまたはSQL_NTSのバイト長、バイナリ バッファーにバインドされた列のデータのバイト長、および NULL に設定される列のSQL_NULL_DATAです。 アプリケーションは、デフォルト (存在する場合) または NULL (存在しない場合) に設定される列の長さ/標識バッファーの値をSQL_COLUMN_IGNOREに設定します。  
  
4.  [操作] 引数を*Operation*SQL_FETCH_BY_BOOKMARKに設定して**SQLBulkOperations**を呼び出します。  
  
 アプリケーションが行操作配列を使用して、特定の列に対して操作が実行されないようにする必要はありません。 アプリケーションは、バインドされたブックマーク配列にそれらの行のブックマークのみをコピーすることによって、フェッチする行を選択します。
