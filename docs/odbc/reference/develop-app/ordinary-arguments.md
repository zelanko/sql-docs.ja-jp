---
title: 通常の引数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 997604b4376656d36d2bc4bc31f1959aa6c8a229
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987820"
---
# <a name="ordinary-arguments"></a>通常の引数
カタログ関数文字列引数が通常の引数の場合は、リテラル文字列として扱われます。 通常の引数は、文字列検索パターンも値のリストも受け入れません。 通常の引数の大文字と小文字が区別され、文字列内の引用符が文字どおりに使用されます。 SQL_ATTR_METADATA_ID statement 属性が SQL_FALSE に設定されている場合、これらの引数は通常の引数として扱われます。この属性が SQL_TRUE に設定されている場合は、代わりに識別子引数として扱われます。  
  
 通常の引数が null ポインターに設定され、引数が必須の引数である場合、関数は SQL_ERROR と SQLSTATE HY009 (null ポインターの無効な使用) を返します。 通常の引数が null ポインターに設定され、引数が必須の引数でない場合、引数の動作はドライバーに依存します。 次の表に、必要な引数を示します。  
  
|Function|必須の引数|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*テーブル*|  
|**SQLForeignKeys**|*Pktablename*、 *FKTableName*|  
|**SQLPrimaryKeys**|*テーブル*|  
|**SQLSpecialColumns**|*テーブル*|  
|**SQLStatistics**|*テーブル*|
