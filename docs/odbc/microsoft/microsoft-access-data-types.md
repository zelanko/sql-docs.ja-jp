---
title: "Microsoft Access データの種類 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 48f7a518f02cd37d1f41a539fc70750c834a3a57
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="microsoft-access-data-types"></a>Microsoft Access データ型
次の表は、Microsoft Access データの型、テーブルを作成するために使用されるデータ型および ODBC SQL データ型を示します。  
  
|Microsoft Access のデータ型|データ型 (CREATETABLE)|ODBC SQL データ型|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY [1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|カウンター|カウンター|SQL_INTEGER|  
|通貨|通貨|SQL_NUMERIC|  
|日付/時刻|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|長いバイナリ|LONGBINARY|SQL_LONGVARBINARY|  
|長いテキスト|長いテキスト|[2] の SQL_LONGVARCHAR SQL_WLONGVARCHAR [3]|  
|メモ|長いテキスト|[2] の SQL_LONGVARCHAR SQL_WLONGVARCHAR [3]|  
|数 (フィールド = 単一)|1 つ|SQL_REAL|  
|数 (フィールド = 倍)|DOUBLE|SQL_DOUBLE|  
|数 (フィールド = バイト)|符号なしバイト|SQL_TINYINT|  
|数 (フィールド サイズが整数型)|短い|SQL_SMALLINT|  
|数 (フィールド長整数を =)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE●ole○|LONGBINARY|SQL_LONGVARBINARY|  
|[TEXT]|VARCHAR|[1] SQL_VARCHAR SQL_WVARCHAR [2]|  
ARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] 4.0 アプリケーションのみにアクセスします。 4,000 バイトの最大長。 LONGBINARY のような動作です。  
  
 [2] は、ANSI アプリケーションだけです。  
  
 [Unicode 3] とアクセス 4.0 アプリケーションだけです。  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC データ型を返します。 1 つ以上の Microsoft Access 型が同じ ODBC SQL データ型にマップされている場合すべての Microsoft Access データ型は返されません。 付録 d のすべての変換、 *ODBC プログラマ リファレンス*の前の表に示す SQL データ型はサポートされます。  
  
 次の表は、Microsoft Access データ型の制限事項を示します。  
  
|データ型|Description|  
|---------------|-----------------|  
|BINARY、VARBINARY、および VARCHAR|ゼロの BINARY、VARBINARY、または VARCHAR 列を作成するか、未指定の長さが実際に 510 バイトの列を返します。|  
|BYTE|フィールド サイズをバイトと同じ Microsoft アクセス番号のフィールドが符号付きでない場合でも、Microsoft Access ドライバーを使用する場合は負の数値は、フィールドに挿入できます。|  
|CHAR、VARCHAR、LONGVARCHAR、|文字の文字列リテラルには、(1 ~ 255 の 10 進数) の任意の ANSI 文字を含めることができます。 2 つの連続する単一引用符 (") を使用して、1 つの単一引用符 (') を表します。<br /><br /> 文字データ型の列で特殊文字を使用するときに、文字データを渡すには、プロシージャを使用してください。|  
|[DATE]|日付の値では、する、ODBC 標準の日付形式に従って区切られたか、または datetime の区切り記号 (「#」) で区切られた必要があります。 それ以外の場合、Microsoft Access を使用して、算術式として値を処理は、警告またはエラーは発生しません。<br /><br /> たとえば、日付として「1996 年 3 月 5 日」を表す必要がある {d ' 1996-03-05'} または #03/05/&#1996; です。それ以外の場合のみ 03/05/1993 が送信されると、Microsoft Access はこれを 1996年で割った値 5 で割ると 3 として評価されます。 この値が 0、整数へ丸めます、これには、使用される日付をゼロ日は、1899-12-31 をマップするためです。<br /><br /> パイプ文字 (&#124;) に戻るの引用符に囲まれている場合でも、日付の値では使用できません。|  
|GUID|データ型が Microsoft Access 4.0 に制限されます。|  
|NUMERIC|データ型が Microsoft Access 4.0 に制限されます。|  
  
 データ型に複数の制限事項は含まれて[データ型の制限事項](../../odbc/microsoft/data-type-limitations.md)です。
