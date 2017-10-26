---
title: "テキスト ファイル データの種類 |Microsoft ドキュメント"
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
- text file driver [ODBC], data types
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- text file data types [ODBC]
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: e113112e-ae42-469e-8e4b-a365a10d9071
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cd72cc24ff011559addeabd0bcc95b172db1a60f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="text-file-data-types"></a>テキスト ファイルのデータ型
次の表では、テキスト データ型を ODBC SQL データ型にマップする方法を示します。 すべての ODBC SQL データ型は、テキストの ODBC ドライバーでサポートされていることに注意してください。  
  
|テキストのデータ型|ODBC データ型|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|[FLOAT]|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC データ型を返します。 付録 d のすべての変換、 *ODBC プログラマ リファレンス*の前の表に示す SQL データ型はサポートされます。  
  
 次の表は、テキスト データ型に制限事項を示します。  
  
|データ型|Description|  
|---------------|-----------------|  
|CHAR|ゼロの char 型の列を作成するか、未指定の長さが実際に 255 ビット列を返します。<br /><br /> 区切られたファイルは、char 型の列が可能性があります。 または先頭と末尾; 二重引用符区切り記号がない可能性があります。固定長のファイルの区切り記号として二重引用符は使用されません。|  
|DATETIME|MM DD-YY (たとえば、92-01-17)<br /><br /> MMM DD YY (たとえば、年 1 月の 17-92)<br /><br /> DD-MMM-年 (たとえば、17-年 1 月-92)<br /><br /> (たとえば、1992-01-17) YYYY MM DD<br /><br /> YYYY MMM-DD (たとえば、1992 年 1 月の 17)<br /><br /> テーブル内で混在した日付の区切り記号を設定することはできません。<br /><br /> テキスト ISAM は、Windows コントロール パネルの 国際対応の設定に応じて、米国とヨーロッパの形式で、DATETIME フィールドを書式設定します。|  
|[FLOAT]|最大の幅には、符号および小数点が含まれます。 Schema.ini、幅が次のように表されます。<br /><br /> 14.083 は FLOAT 幅 6 です。<br /><br /> -14.083 は FLOAT 幅 7 です。<br /><br /> +14.083 は FLOAT 幅 7 です。<br /><br /> 14083。 FLOAT 幅 6 は、します。<br /><br /> ODBC では、8 float 型の列を常に返します。<br /><br /> FLOAT 列こともできます、科学的表記法で例を示します。<br /><br /> -3.04E + 2 は Float 幅 8<br /><br /> 25E4 は Float 幅 4 です。<br /><br /> **注**列に 10 進数と指数表記を混在させることはできません。<br /><br /> NULL 値は、固定長ファイル内の空白の埋め込み文字列で表されます、区切られたファイルで除外されます。<br /><br /> Float 型データは、先行する空白が埋め込まれていることができます。|  
|INTEGER|整数型の列の有効な値は、-32766 に 32767 です。<br /><br /> Schema.ini、幅が次のように表されます。<br /><br /> 14083 は整数幅 5 です。<br /><br /> 0 は整数幅 1 です。<br /><br /> ODBC は、常に整数型の列には 4 を返します。<br /><br /> 最大の幅には、符号が含まれています。 整数型の列の最大の幅は 11 は幅は固定形式のテーブルで許可される空白により大きくすることも可能です。|  
|LONGCHAR|固定長のいずれかで LONGCHAR 列の幅に、理論的な制限または区切り記号付きのテーブルが 65500 K です。 テキスト ISAM は、最大で約 32 K の信頼性の高いサポートを提供する可能性が高くなります。|  
  
 データ型に複数の制限事項は含まれて[データ型の制限事項](../../odbc/microsoft/data-type-limitations.md)です。

