---
title: パラドックスデータ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a85cf643a6d22b9b2fce15984539d74dc43c62ab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290932"
---
# <a name="paradox-data-types"></a>Paradox データ型
ODBC パラドックス ドライバーは、パラドックスのデータ型を ODBC SQL データ型にマップします。 次の表は、すべての Paradox データ型と、それらがマップされている ODBC SQL データ型を示しています。  
  
|パラドックスデータ型|ODBC データ型|  
|-----------------------|--------------------|  
|英数字|SQL_VARCHAR|  
|オートインクリメント[1]|SQL_INTEGER|  
|BCD[1]|SQL_DOUBLE|  
|バイト[1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|画像[2]|SQL_LONGVARBINARY|  
|論理[1]|SQL_BIT|  
|ロング[1]|SQL_INTEGER|  
|メモ[2]|SQL_LONGVARCHAR|  
|お金[1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|SHORT|SQL_SMALLINT|  
|時間[1]|SQL_TIMESTAMP|  
|タイムスタンプ[1]|SQL_TIMESTAMP|  
  
 [1] パラドックスバージョン 5 に対してのみ有効です。*x .*  
  
 [2] パラドックスバージョン4でのみ有効です。*x*および 5.*x .*  
  
> [!NOTE]  
>  ODBC SQL データ**型を**返します。 *ODBC プログラマ リファレンス*の付録 D のすべての変換は、このトピックで前述した ODBC SQL データ型でサポートされています。  
  
 次の表は、Paradox データ型の制限を示しています。  
  
|データ型|説明|  
|---------------|-----------------|  
|英数字|ゼロまたは未指定の長さの ALPHANUMERIC 列を作成すると、実際には 255 バイトの列が戻されます。|  
|BYTES|Paradox5 ドライバを使用してバイナリ列に NULL を挿入すると、0 に変更されます。|  
|LONG|Paradox 5 の Long データ型の Paradox ドライバでサポートされている最大負の値。SQL_INTEGER *x*は -2^31 (-2147483648) ではありません。 Long でサポートされる最大負の値は、実際には -2^31 + 1 (-2147483647) です。|  
|timestamp|Paradox ドライバによって TIMESTAMP 列に値が挿入され、その後列から取得された場合、取得した値は丸め処理のために挿入された値と 1 秒だけ異なる場合があります。|  
  
 データ型に関するその他の制限については、「[データ型の制限](../../odbc/microsoft/data-type-limitations.md)」を参照してください。
