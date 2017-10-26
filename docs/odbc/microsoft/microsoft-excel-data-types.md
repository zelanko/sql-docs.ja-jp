---
title: "Microsoft Excel データの種類 |Microsoft ドキュメント"
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
- data types [ODBC], Excel driver
- Excel data types [ODBC]
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], data types
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eeb2bc72ce34141eb3dbdca3f952dca0c476c2dd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-excel-data-types"></a>Microsoft Excel のデータ型
次の表では、Microsoft Excel ドライバーのデータ型を ODBC SQL データ型にマップする方法を示します。 Microsoft Excel ドライバーでは、列のデータに基づく Microsoft Excel のテーブル内の列にこれらのデータ型が割り当てられます。  
  
|Microsoft Excel のデータ型|ODBC データ型|  
|-------------------------------|--------------------|  
|通貨|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|論理|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|[TEXT]|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC SQL データ型を返します。 付録 d のすべての変換、 *ODBC プログラマ リファレンス*このトピックの前半に示した ODBC SQL データ型はサポートされます。  
  
 次の表は、Microsoft Excel のデータ型に制限事項を示します。  
  
|データ型|Description|  
|---------------|-----------------|  
|暗号化データ|Microsoft Excel ドライバーでは、暗号化されたデータを読み取ることができません。|  
|エラー文字列|Microsoft Excel ドライバーは、Microsoft Excel のエラー値を文字の文字列を返すことはできません (#n/a!、#value!!、#REF!、#DIV/0!、#num!!、#NAME?、および #NULL!)、代わりに NULL を返しますが、します。|  
|論理|論理列の値は、0 または 1 のいずれかとして SQL_C_CHAR バッファーに返されます。|  
|NUMBER|整数型の列を作成する場合、整数データ型に対して大きすぎますされる番号を入力することができます、および可能性がありますに列 SQL_DOUBLE に変換することは結果と共に、非整数の値を含むデータを挿入することができます。|  
|[TEXT]|列の行には、1 つ以上の Microsoft Excel のデータ型が含まれて、Microsoft Excel の ODBC ドライバーは、列に SQL_VARCHAR データ型を割り当てます。 1 つの例外がある: Microsoft Excel の ODBC ドライバーが列に、SQL_TIMESTAMP データ型を割り当て、datetime データ型 (日付、時刻、および DATETIME) の 3 つまたは 2 つだけが、列が含まれる場合。<br /><br /> 0 のテキスト列を作成するか、未指定の長さが実際に 255 バイトの列を返します。<br /><br /> 文字の文字列リテラルには、(1 ~ 255 の 10 進数) の任意の ANSI 文字を含めることができます。 2 つの連続する単一引用符 (") を使用して、1 つの単一引用符 (') を表します。<br /><br /> SQL_VARCHAR 以外のデータ型の列に NULL を挿入すると、SQL_VARCHAR に変更する列のデータ型が発生します。|  
  
 データ型に複数の制限事項は含まれて[データ型の制限事項](../../odbc/microsoft/data-type-limitations.md)です。

