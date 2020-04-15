---
title: SQL コル属性 (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9508fa7b9ada8273e1250d7584e577892acf5c51
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307913"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: コア レベル  
  
 結果セット内の列の記述子情報を返します。 記述子情報は、文字ストリング、32 ビット記述子依存値、または整数値として戻されます。  
  
> [!NOTE]  
>  **SQLColAttributes**を使用して、ブックマーク列 (列 0) に関する情報を返すことはできません。  
  
 ビジュアル フォックスプロ ODBC ドライバーは、すべての*fDescType 値をサポートしています*。 次の表に、選択した値のドライバーの実装に関するコメントを示します。  
  
|*fDesc タイプ*|解説|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|FALSE を返します: ビジュアル FoxPro にはカウンター フィールドがありません。|  
|SQL_COLUMN_CASE_SENSITIVE|列の型が文字型の場合は常に TRUE を返します。|  
|SQL_COLUMN_LABEL|SQL_COLUMN_NAMEによっても返される列名を返します。|  
|SQL_COLUMN_MONEY|列の型が通貨 (Visual FoxPro 言語では "Y" で表される) の場合は TRUE を返します。|  
|SQL_COLUMN_OWNER_NAME|常に空の文字列を返します。|  
|SQL_COLUMN_QUALIFIER_NAME|常に空の文字列を返します。|  
|SQL_COLUMN_SEARCHABLE|型の列のSQL_UNSEARCHABLEを返します。これらの列は WHERE 句では使用できません。<br /><br /> 型の文字またはメモ型の列に対して SQL_SEARCHABLEを返します。これらの列は、任意の比較演算子を使用して WHERE 句で使用できます。<br /><br /> その他のすべての列型のSQL_ALL_EXCEPT_LIKEを返します。これらの列は、LIKE 以外のすべての比較演算子を使用して WHERE 句で使用できます。|  
|SQL_COLUMN_TABLE_NAME|常に空の文字列を返します。|  
  
 詳細については *、ODBC プログラマ リファレンス*の[SQLCol 属性](../../odbc/reference/syntax/sqlcolattributes-function.md)を参照してください。
