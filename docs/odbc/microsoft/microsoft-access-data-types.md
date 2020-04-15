---
title: Access のデータ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 024fb65b6fdc81ae0a8e007d1cee150c6a35b91c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307731"
---
# <a name="microsoft-access-data-types"></a>Microsoft Access データ型
次の表は、Access のデータ型、テーブルの作成に使用されるデータ型、および ODBC SQL データ型を示しています。  
  
|Access データ型|データ型 (CREATETABLE)|ODBC SQL データ型|  
|--------------------------------|-------------------------------|------------------------|  
|ビッグバイナリ[1]|ロングバイナリ|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|カウンター|カウンター|SQL_INTEGER|  
|通貨|通貨|SQL_NUMERIC|  
|日付/時刻|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|長いバイナリ|ロングバイナリ|SQL_LONGVARBINARY|  
|長いテキスト|長いテキスト|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|メモ|長いテキスト|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|数値 (フィールドサイズ = シングル)|単一|SQL_REAL|  
|数値 (フィールドサイズ = ダブル)|DOUBLE|SQL_DOUBLE|  
|数値 (フィールドサイズ = バイト)|符号なしバイト|SQL_TINYINT|  
|数値 (フィールドサイズ = 整数)|SHORT|SQL_SMALLINT|  
|数値 (フィールドサイズ = 長整数)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE●ole○|ロングバイナリ|SQL_LONGVARBINARY|  
|[TEXT]|VARCHAR|SQL_VARCHAR[1] SQL_WVARCHAR[2]|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] 4.0 アプリケーションのみにアクセスします。 最大長は 4000 バイトです。 ロングバイナリに似た動作。  
  
 [2] ANSI アプリケーションのみ。  
  
 [3] ユニコードおよび Access 4.0 アプリケーションのみ。  
  
> [!NOTE]  
>  ODBC**データ型を**返します。 複数の Access 型が同じ ODBC SQL データ型にマップされている場合、Access のデータ型の一覧は返されません。 *ODBC プログラマ リファレンス*の付録 D のすべての変換は、前の表に示した SQL データ型でサポートされています。  
  
 次の表は、Access のデータ型に関する制限を示しています。  
  
|データ型|説明|  
|---------------|-----------------|  
|バイナリ、VAR バイナリ、および VARCHAR|BINARY、VARBINARY、または VARCHAR 列の長さが 0 または不特定の列を作成すると、実際には 510 バイトの列が戻されます。|  
|BYTE|Byte に等しいフィールドサイズの Access NUMBER フィールドが符号なしの場合でも、Access ドライバを使用する場合は、フィールドに負の数を挿入できます。|  
|文字、長いバールチャー、およびヴァルチャー|文字ストリング・リテラルには、任意の ANSI 文字 (1 から 255 桁) を入れることができます。 単一引用符 (') を 1 つ表すには、2 つの連続した単一引用符 (') を使用します。<br /><br /> 文字データ型列で特殊文字を使用する場合は、プロシージャを使用して文字データを渡す必要があります。|  
|DATE|日付値は、ODBC 標準の日付形式に従って区切るか、日時区切り文字 ("#") で区切る必要があります。 それ以外の場合は、値が演算式として扱われ、警告やエラーは発生しません。<br /><br /> たとえば、日付 "1996 年 3 月 5 日" は {d '1996-03-05'} または #03/05/1996# として表す必要があります。それ以外の場合、1993/03/05 のみが送信された場合、Access では、これを 1996 年によって 5 で割った値で 3 と評価されます。 この値は整数 0 に切り上げ、ゼロ日は 1899-12-31 にマップされるため、これは使用される日付です。<br /><br /> 戻る引用符で囲まれていても、パイプ文字 (&#124;) を日付値で使用することはできません。|  
|GUID|Access 4.0 に制限されたデータ型です。|  
|NUMERIC|Access 4.0 に制限されたデータ型です。|  
  
 データ型に関するその他の制限については、「[データ型の制限](../../odbc/microsoft/data-type-limitations.md)」を参照してください。
