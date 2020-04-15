---
title: テキスト ファイルデータ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], data types
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- text file data types [ODBC]
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: e113112e-ae42-469e-8e4b-a365a10d9071
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7864dc81eaa3dd37f3d0053b2329c8842e445c8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302660"
---
# <a name="text-file-data-types"></a>テキスト ファイルのデータ型
次の表は、テキスト データ型が ODBC SQL データ型にマップされる方法を示しています。 ODBC テキスト ドライバーでサポートされている ODBC SQL データ型の一覧もあります。  
  
|テキスト データ型|ODBC データ型|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|ロングチャー|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  ODBC**データ型を**返します。 *ODBC プログラマ リファレンス*の付録 D のすべての変換は、前の表に示した SQL データ型でサポートされています。  
  
 次の表は、テキストデータ型の制限を示しています。  
  
|データ型|説明|  
|---------------|-----------------|  
|CHAR|ゼロまたは未指定の長さの CHAR 列を作成すると、実際には 255 ビット列が戻されます。<br /><br /> 区切りファイルでは、CHAR 列の先頭と末尾に二重引用符区切り文字が含まれる場合と、二重引用符区切り文字が含まれていない場合があります。固定長ファイルでは、二重引用符は区切り文字として使用されません。|  
|DATETIME|MM-DD-YY (例えば、01-17-92)<br /><br /> MMM-DD-YY (例: 1 月 17-92)<br /><br /> DD-MMM-YY (例: 17-1-92)<br /><br /> YYYY-MM-DD (例: 1992-01-17)<br /><br /> YYYY-MMM-DD(例えば、1992-1月-17)<br /><br /> テーブル内では、日付の区切り記号を混在させることはできません。<br /><br /> テキスト ISAM は、Windows のコントロール パネルの [国際] の設定に応じて、米国またはヨーロッパの形式で DATETIME フィールドをフォーマットします。|  
|FLOAT|最大幅には、符号と小数点が含まれます。 スキーマ.iniでは、幅は次のように表示されます。<br /><br /> 14.083 は FLOAT 幅 6<br /><br /> -14.083 は FLOAT 幅 7 です<br /><br /> +14.083 は FLOAT 幅 7<br /><br /> 14083. は FLOAT 幅 6<br /><br /> ODBC は FLOAT 列に対して常に 8 を返します。<br /><br /> FLOAT 列は、次の例に示す指数表記の場合もあります。<br /><br /> -3.04E+2 はフロート幅 8<br /><br /> 25E4はフロート幅4<br /><br /> **注**10 進表記と指数表記は、列に混在させることはできません。<br /><br /> NULL 値は、固定長ファイルでは空白の埋め込み文字列で表され、区切りファイルでは省略されます。<br /><br /> 浮動データには先行ブランクを埋め込むことができます。|  
|INTEGER|INTEGER 列の有効な値は 32767 から -32766 です。<br /><br /> スキーマ.iniでは、幅は次のように表示されます。<br /><br /> 14083 は整数幅 5 です<br /><br /> 0 は整数幅 1<br /><br /> ODBC は、整数型の列に対して常に 4 を返します。<br /><br /> 最大幅には符号が含まれます。 INTEGER 列の最大幅は 11 ですが、固定形式の表で使用できるブランクが原因で幅が大きくなる可能性があります。|  
|ロングチャー|固定長または区切りテーブルの LONGCHAR カラムの幅に関する理論上の制限値は 65500K です。 テキスト ISAM は、約 32 K までの信頼性の高いサポートを提供する可能性が高くなります。|  
  
 データ型に関するその他の制限については、「[データ型の制限](../../odbc/microsoft/data-type-limitations.md)」を参照してください。
