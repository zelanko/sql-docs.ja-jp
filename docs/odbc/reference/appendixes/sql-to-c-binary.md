---
title: "SQL には、c: バイナリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ccb6114eab57030d6555931f0bfcdbe469326442
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-binary"></a>SQL には、c: バイナリ
バイナリの ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 次の表は、ODBC C データ型の SQL のバイナリ データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(データのバイト長)\* 2 < *BufferLength*<br /><br /> (データのバイト長)\* 2 > = *BufferLength*|data<br /><br /> 切り捨てられたデータ|バイト単位でデータの長さ<br /><br /> バイト単位でデータの長さ|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|(データの文字長)\* 2 < *BufferLength*<br /><br /> (データの文字長)\* 2 > = *BufferLength*|data<br /><br /> 切り捨てられたデータ|データの文字の長さ<br /><br /> データの文字の長さ|n/a<br /><br /> 01004|  
|SQL_C_BINARY|データのバイト長 < = *BufferLength*<br /><br /> データのバイト長 > *BufferLength*|data<br /><br /> 切り捨てられたデータ|バイト単位でデータの長さ<br /><br /> バイト単位でデータの長さ|n/a<br /><br /> 01004|  
  
 SQL のバイナリ データが文字データに変換されると、ソース データの各バイト (8 ビット) は 2 つの ASCII 文字として表されます。 これらの文字は、16 進表現内の数値の ASCII 文字の表現です。 たとえば、バイナリ 00000001 は「01」に変換され、バイナリ 11111111 は"FF"に変換されます。  
  
 常に、ドライバーは、個々 のバイトを 16 進数字のペアに変換し、null バイトの文字の文字列を終了します。 このため場合、 *BufferLength*でもは、変換後のデータの最後のバイトの長さより小さい、**TargetValuePtr*バッファーは使用されません。 (変換後のデータが偶数のバイトを必要と、次への最後のバイトを null バイトと最後のバイトを使用することはできません。)  
  
> [!NOTE]  
>  アプリケーション開発者は、文字 C データ型をバイナリの SQL データをバインドしないでください。 この変換は、非効率的で低速では通常です。

