---
title: dBASE データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17b96ad0b6674a2d120ef46d9bfa221e8df6d140
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307693"
---
# <a name="dbase-data-types"></a>dBASE データ型
次の表は、dBASE データ型が ODBC SQL データ型にマップされる方法を示しています。 ODBC SQL データ型の一つには、サポートされていない点に注意してください。  
  
|dBASE データ型|ODBC データ型|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|フロート[1]|SQL_DOUBLE|  
|論理|SQL_BIT|  
|メモ|SQL_LONGVARCHAR|  
|数値 (BCD)|SQL_DOUBLE|  
|OLEオブジェクト[1]|SQL_LONGBINARY|  
  
 [1] dBASE バージョン 5 に対してのみ有効です。*x*  
  
 dBASE III の精度では、最大 2 桁の指数と dBASE IV 番号の数値を最大 3 桁の指数で指定できます。 数値は文字列として格納されるため、数値に変換されます。 変換する数値がフィールドに収まらない場合は、原因不明の結果が発生する可能性があります。  
  
 dBASE では、精度と小数点以下桁数を NUMERIC データ型で指定できますが、ODBC dBASE ドライバではサポートされていません。 ODBC dBASE ドライバは、NUMERIC データ型の場合、常に精度 15、小数点以下桁数 0 を返します。  
  
 ODBC dBASE ドライバーを使用して数値データ型で作成された列は、ODBC データ型SQL_DOUBLEにマップされます。 したがって、この列のデータは丸めの対象となります。 この動作は、dBASE (タイプ N) の NUMERIC データ型の場合とは同じではありません。  
  
> [!NOTE]  
>  ODBC SQL データ**型を**返します。 *ODBC プログラマ リファレンス*の付録 D のすべての変換は、このトピックで前述した ODBC SQL データ型でサポートされています。  
  
 次の表は、dBASE データ型の制限を示しています。  
  
|データ型|説明|  
|---------------|-----------------|  
|CHAR|ゼロまたは未指定の長さの CHAR 列を作成すると、実際には 254 バイトの列が戻されます。|  
|暗号化データ|dBASE ドライバは暗号化された dBASE テーブルをサポートしていません。|  
|論理|dBASE ドライバーは、論理列のインデックスを作成できません。|  
|メモ|MEMO 列の最大長は 65,500 バイトです。|  
  
 データ型に関するその他の制限については、「[データ型の制限](../../odbc/microsoft/data-type-limitations.md)」を参照してください。
