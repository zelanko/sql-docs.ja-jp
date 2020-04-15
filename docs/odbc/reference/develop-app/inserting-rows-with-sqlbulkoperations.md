---
title: SQLBulk 操作を使用した行の挿入 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a6fa384292f02026b8390aa92525144dce6f549b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300112"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>SQLBulkOperations による行の挿入
**SQLBulkOperations を**使用したデータの挿入は、バインドされたアプリケーション バッファーからのデータを使用するため **、SQLBulkOperations**を使用したデータの更新に似ています。  
  
 新しい行の各列に値が設定されるようにするには、長さ/インジケーター値が SQL_COLUMN_IGNORE で、すべての非連結列が NULL 値を受け入れるか、デフォルトを持つ必要があります。  
  
 **SQLBulkOperations**を使用して行を挿入するには、アプリケーションは次の処理を行います。  
  
1.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性を挿入する行数に設定し、バインドされたアプリケーション バッファーに新しいデータ値を格納します。 **長**いデータを送信する方法の詳細については、「[長いデータと SQL セットポスと SQLBulk オペレーション](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)」を参照してください。  
  
2.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、文字列バッファーにバインドされた列のデータまたはSQL_NTSのバイト長、バイナリ バッファーにバインドされた列のデータのバイト長、および NULL に設定される列のSQL_NULL_DATAです。 アプリケーションは、デフォルト (存在する場合) または NULL (存在しない場合) に設定される列の長さ/標識バッファーの値をSQL_COLUMN_IGNOREに設定します。  
  
3.  引数をSQL_ADD に設定*Operation*して**SQLBulkOperations**を呼び出します。  
  
 SQLBulk**オペレーションが**戻った後、現在の行は変更されません。 ブックマーク列 (列 0) がバインドされている場合 **、SQLBulkOperations はその**列にバインドされた行セット バッファーに挿入された行のブックマークを返します。
