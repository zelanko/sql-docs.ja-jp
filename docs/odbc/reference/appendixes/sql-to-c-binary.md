---
title: 'SQL から C へ: バイナリ |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b0ce72f650e61b83ec99b0727752612d18da52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298827"
---
# <a name="sql-to-c-binary"></a>SQL から C へ: Binary
バイナリ ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 次の表は、バイナリ SQL データの変換先となる ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(データのバイト長)\* 2 <*バッファ長*<br /><br /> (データのバイト長)\* 2 >=*バッファ長*|Data<br /><br /> 切り捨てられたデータ|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)|該当なし<br /><br /> 01004|  
|SQL_C_WCHAR|(データの文字長)\* 2 <*バッファ長*<br /><br /> (データの文字長)\* 2 >=*バッファ長*|Data<br /><br /> 切り捨てられたデータ|文字でのデータの長さ<br /><br /> 文字でのデータの長さ|該当なし<br /><br /> 01004|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 切り捨てられたデータ|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)|該当なし<br /><br /> 01004|  
  
 バイナリSQLデータが文字Cデータに変換される場合、ソースデータの各バイト(8ビット)は2つのASCII文字として表されます。 これらの文字は、16 進形式の数字の ASCII 文字表現です。 たとえば、バイナリ 00000001 は "01" に変換され、バイナリ 1111111 は "FF" に変換されます。  
  
 ドライバーは、常に個々のバイトを 16 進数のペアに変換し、null バイトで文字列を終了します。 このため *、BufferLength*が偶数であり、変換されたデータの長さより小さい場合、**TargetValuePtr*バッファーの最後のバイトは使用されません。 (変換されたデータには偶数バイトが必要で、次のバイトから最後のバイトは NULL バイトであり、最後のバイトは使用できません)。  
  
> [!NOTE]  
>  アプリケーション開発者は、バイナリ SQL データを文字 C データ型にバインドすることはお勧めしません。 この変換は、通常、非効率的で低速です。
