---
title: ブックマークによる行の更新 SQLBulk オペレーション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], updating rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9c755297e8beadad92b5be81d78ca534bb96ecae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283200"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>SQLBulkOperations を使ったブックマークによる行の更新
ブックマークによって行を更新する場合 **、SQLBulkOperations は**、テーブルの 1 つまたは複数の行を更新するデータ ソースを作成します。 行は、バインドされたブックマーク列のブックマークによって識別されます。 行は、バインドされた各列のアプリケーション・バッファー内のデータを使用して更新されます (ただし、列の長さ/標識バッファーの値がSQL_COLUMN_IGNORE場合を除く)。 非バインド列は更新されません。  
  
 **SQLBulkOperations**を使用してブックマークによって行を更新するには、次の手順を実行します。  
  
1.  更新するすべての行のブックマークを取得してキャッシュします。 複数のブックマークがあり、列方向のバインドが使用される場合、ブックマークは配列に格納されます。複数のブックマークがあり、行方向のバインドが使用されている場合、ブックマークは行構造の配列に格納されます。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性をブックマークの数に設定し、ブックマーク値またはブックマークの配列を含むバッファーを列 0 にバインドします。  
  
3.  新しいデータ値を行セット バッファーに配置します。 **長**いデータを送信する方法の詳細については、「[長いデータと SQL セットポスと SQLBulk オペレーション](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)」を参照してください。  
  
4.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、文字列バッファーにバインドされた列のデータまたはSQL_NTSのバイト長、バイナリ バッファーにバインドされた列のデータのバイト長、および NULL に設定される列のSQL_NULL_DATAです。  
  
5.  SQL_COLUMN_IGNOREに更新されない列の長さ/インジケーター バッファーの値を設定します。 アプリケーションはこの手順をスキップして既存のデータを再送信できますが、これは非効率的であり、読み取り時に切り捨てられたデータ ソースに値を送信するリスクがあります。  
  
6.  引数を SQL_UPDATE_BY_BOOKMARK に*Operation*設定して**SQLBulkOperations**を呼び出します。  
  
 更新としてデータ ソースに送信されるすべての行に対して、アプリケーション バッファーに有効な行データが必要です。 アプリケーション・バッファーがフェッチによって満たされた場合、行状況配列が維持され、行の状況値がSQL_ROW_DELETED、SQL_ROW_ERROR、またはSQL_ROW_NOROW場合、無効なデータが誤ってデータ・ソースに送信される可能性があります。
