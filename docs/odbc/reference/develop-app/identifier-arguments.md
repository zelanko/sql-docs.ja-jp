---
title: 識別子の引数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- identifier arguments [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], identifier
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6831eab30daebe37baecebe3ed7053537d7de8f8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300162"
---
# <a name="identifier-arguments"></a>識別子の引数
識別子引数の文字列が引用符で囲まれている場合、ドライバーは先頭と末尾の空白を削除し、引用符で囲まれた文字列をそのまま扱います。 文字列が引用符で囲まれていない場合、ドライバーは末尾の空白を削除し、文字列を大文字に折り返します。 識別子の引数をヌル・ポインターに設定すると、SQL_ERRORおよび SQLSTATE HY009 (ヌル・ポインターの無効な使用) が戻されます( 引数がカタログ名であり、カタログがサポートされない場合)。  
  
 SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定されている場合、これらの引数は識別子引数として扱われます。 この場合、アンダースコア (_) とパーセント記号 (%)検索パターン文字としてではなく、実際の文字として扱われます。 この属性がSQL_FALSEに設定されている場合、引数に応じて、これらの引数は通常の引数またはパターン引数として扱われます。  
  
 特殊文字を含む識別子は SQL ステートメントで引用符で囲む必要がありますが、カタログ関数に渡される引用符文字は文字どおりに解釈されるため、カタログ関数引数として渡されるときに引用符で囲む必要はありません。 たとえば、識別子の引用符文字 (ドライバー固有で**SQLGetInfo**を介して返される) が二重引用符 (") であるとします。 **SQLTables**の最初の呼び出しは、買掛金勘定テーブルに関する情報を含む結果セットを返しますが、2 番目の呼び出しは "買掛金勘定" テーブルに関する情報を返しますが、これは意図したものとは考えがちではありません。  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 引用符で囲まれた識別子は、Oracle の ROWID など、同じ名前の疑似列と真の列名を区別するために使用されます。 カタログ関数の引数に "ROWID" が渡された場合、この関数は ROWID 疑似列が存在する場合は処理されます。 疑似列が存在しない場合、この関数は "ROWID" 列で動作します。 ROWID がカタログ関数の引数で渡された場合、この関数は ROWID 列を処理します。  
  
 引用符で囲まれた識別子の詳細については、「[引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)」を参照してください。
