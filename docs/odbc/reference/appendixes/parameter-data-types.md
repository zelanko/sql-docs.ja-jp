---
title: パラメータ データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: f29bb70937df32e03480c13c7ef739eb273f15eb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303583"
---
# <a name="parameter-data-types"></a>パラメーターのデータ型
**SQLBindParameter**で指定された各パラメーターは SQL データ型を使用して定義されていますが、SQL ステートメントのパラメーターには組み込みデータ型がありません。 したがって、パラメーター・マーカーを SQL ステートメントに組み込むことができるのは、そのデータ・タイプがステートメント内の別のオペランドから推論できる場合のみです。 たとえば、 ? などの算術式の中で、 ? + COLUMN1 は、パラメータのデータ型を COLUMN1 で表される名前付きカラムのデータ型から推論できます。 データ型を決定できない場合、アプリケーションはパラメーター マーカーを使用できません。  
  
 次の表では、SQL-92 に従って、いくつかのタイプのパラメーターについてデータ型を決定する方法について説明します。 他の SQL 文節が使用される場合のパラメーター・タイプの推論に関するより包括的な仕様については、SQL-92 仕様を参照してください。  
  
|パラメータの場所|想定されるデータ型|  
|---------------------------|-----------------------|  
|2 項算術演算子または比較演算子の 1 つのオペランド|他のオペランドと同じ|  
|**BETWEEN**句の最初のオペランド|2 番目のオペランドと同じ|  
|**BETWEEN**句の 2 番目または 3 番目のオペランド|最初のオペランドと同じ|  
|**IN**で使用される式|サブクエリの最初の値または結果列と同じ|  
|**IN**で使用される値|式にパラメーター マーカーがある場合は、式または最初の値と同じ|  
|**LIKE**で使用されるパターン値|VARCHAR|  
|**UPDATE**で使用される更新値|更新列と同じ|
