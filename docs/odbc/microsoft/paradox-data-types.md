---
title: "Paradox データ タイプ |Microsoft ドキュメント"
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
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9099d9a84fb79132249c74d1d24cc240bcf8aae0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="paradox-data-types"></a>Paradox データ型
ODBC Paradox ドライバーは、Paradox データ型を ODBC SQL データ型にマップします。 次の表では、Paradox のすべてのデータ型を一覧表示して、ODBC SQL データ型にマップされますを表示します。  
  
|Paradox データ型|ODBC データ型|  
|-----------------------|--------------------|  
|英数字|SQL_VARCHAR|  
|AUTOINCREMENT [1]|SQL_INTEGER|  
|BCD [1]|SQL_DOUBLE|  
|バイト [1]|SQL_BINARY|  
|[DATE]|SQL_DATE|  
|イメージ [2]|SQL_LONGVARBINARY|  
|論理 [1]|SQL_BIT|  
|時間の長い [1]|SQL_INTEGER|  
|メモ [2]|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|短い|SQL_SMALLINT|  
|時間 [1]|SQL_TIMESTAMP|  
|タイムスタンプ [1]|SQL_TIMESTAMP|  
  
 Paradox バージョン 5 に対してのみ有効期間を [1] です。*x*です。  
  
 Paradox バージョン 4 に対してのみ有効期間を [2]。*x*と 5* 。x*です。  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC SQL データ型を返します。 付録 d のすべての変換、 *ODBC プログラマ リファレンス*このトピックの前半に示した ODBC SQL データ型はサポートされます。  
  
 次の表は、Paradox データ型の制限事項を示します。  
  
|データ型|Description|  
|---------------|-----------------|  
|英数字|ゼロの英数字の列を作成するか、未指定の長さが実際に 255 バイトの列を返します。|  
|BYTES|Paradox5 ドライバーとバイナリ列に NULL を挿入する場合は、0 に変更されます。|  
|LONG|Paradox 5 で長い形式のデータ型の Paradox ドライバーでサポートされる負の値の最大値。*x*は-2 ^31 (-2147483648) 必要があります、ODBC のデータを長いマップから入力 SQL_INTEGER です。 長期間サポートされる最大の負の値が実際には-2 ^31 + 1 (-2147483647)。|  
|timestamp|値が、Paradox ドライバーによって TIMESTAMP 列に挿入し、列から取得した後で、取得した値によって異なる場合が値が挿入される 1 秒程度で丸め処理を行うためです。|  
  
 データ型に複数の制限事項は含まれて[データ型の制限事項](../../odbc/microsoft/data-type-limitations.md)です。

