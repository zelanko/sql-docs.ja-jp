---
title: Excel データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], Excel driver
- Excel data types [ODBC]
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], data types
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8574985e10e5aaa3ae5431af7ee1245643e20b60
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283772"
---
# <a name="microsoft-excel-data-types"></a>Microsoft Excel のデータ型
次の表は、Excel ドライバーのデータ型が ODBC SQL データ型にマップされる方法を示しています。 Microsoft Excel ドライバーは、列のデータに基づいて、Microsoft Excel テーブルの列にこれらのデータ型を割り当てます。  
  
|Excel データ型|ODBC データ型|  
|-------------------------------|--------------------|  
|通貨|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|論理|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|[TEXT]|SQL_VARCHAR|  
  
> [!NOTE]  
>  ODBC SQL データ**型を**返します。 *ODBC プログラマ リファレンス*の付録 D のすべての変換は、このトピックで前述した ODBC SQL データ型でサポートされています。  
  
 次の表は、Excel のデータ型に関する制限を示しています。  
  
|データ型|説明|  
|---------------|-----------------|  
|暗号化データ|Excel ドライバは暗号化されたデータを読み取ることができません。|  
|エラー文字列|Microsoft Excel ドライバは、Microsoft Excel のエラー値 (#N/A!、#VALUE!、#REF!、#DIV/0!、#NUM!、#NAME!、#NULL!|  
|論理|LOGICAL 列の値は、0 または 1 として SQL_C_CHAR バッファーに戻されます。|  
|NUMBER|整数列を作成すると、整数データ型に対して大きすぎる数値を入力したり、整数以外の値を含むデータを挿入したり、列をSQL_DOUBLEに変換することができます。|  
|[TEXT]|列の行に複数の Excel データ型が含まれている場合、ODBC Excel ドライバは列にSQL_VARCHARデータ型を割り当てます。 ただし、列に日付/時刻データ型 (DATE、TIME、および DATETIME) が 2 つまたは 3 つしか含まれなかった場合、ODBC Excel ドライバは、SQL_TIMESTAMPデータ型を列に割り当てます。<br /><br /> ゼロまたは未指定の長さの TEXT 列を作成すると、実際には 255 バイトの列が戻されます。<br /><br /> 文字ストリング・リテラルには、任意の ANSI 文字 (1 から 255 桁) を入れることができます。 単一引用符 (') を 1 つ表すには、2 つの連続した単一引用符 (") を使用します。<br /><br /> SQL_VARCHAR以外のデータ型を持つ列に NULL を挿入すると、列のデータ型がSQL_VARCHARに変更されます。|  
  
 データ型に関するその他の制限については、「[データ型の制限](../../odbc/microsoft/data-type-limitations.md)」を参照してください。
