---
title: SQLColAttributes (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee4dc59599053bbbf676f94e8e94540aad83ec82
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 結果セット内の列の記述子の情報を返します。 記述子の情報は、文字の文字列、32 ビットの記述子に依存する値、または整数値として返されます。  
  
> [!NOTE]  
>  **SQLColAttributes**ブックマーク列 (列 0) に関する情報を返すには使用できません。  
  
 Visual FoxPro ODBC ドライバーをすべてサポートしている*fDescType*値。 次の表には、選択した値のドライバーの実装にコメントが含まれています。  
  
|*fDescType*|解説|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|FALSE を返します: Visual FoxPro カウンターにフィールドがありません。|  
|SQL_COLUMN_CASE_SENSITIVE|常に列のデータ型が文字の場合は、TRUE を返します。|  
|SQL_COLUMN_LABEL|SQL_COLUMN_NAME によっても返される列名を返します。|  
|SQL_COLUMN_MONEY|列のデータ型は、通貨 (Visual FoxPro 言語である"Y"で表される) かどうかは TRUE を返します。|  
|SQL_COLUMN_OWNER_NAME|常に空の文字列を返します。|  
|SQL_COLUMN_QUALIFIER_NAME|常に空の文字列を返します。|  
|SQL_COLUMN_SEARCHABLE|SQL_UNSEARCHABLE 全般; 型の列を返します。これらの列は、WHERE 句で使用することはできません。<br /><br /> 文字または NOCPTRANS とメモ型の列を返します SQL_SEARCHABLE 設定されていません。これらの列は、任意の比較演算子と共に WHERE 句で使用できます。<br /><br /> 返します SQL_ALL_EXCEPT_LIKE の他の列の型です。これらの列は、LIKE を除くすべての比較演算子と共に WHERE 句で使用できます。|  
|SQL_COLUMN_TABLE_NAME|常に空の文字列を返します。|  
  
 詳細については、次を参照してください。 [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)で、 *ODBC プログラマ リファレンス*です。
