---
title: 通常の引数 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97362f93e91ccd8b592b4c05a0714b7602c1ba94
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282468"
---
# <a name="ordinary-arguments"></a>通常の引数
カタログ関数の文字列引数が通常の引数の場合、リテラル文字列として扱われます。 通常の引数は、文字列検索パターンも値のリストも受け入れません。 通常の引数の大文字と小文字は重要であり、文字列内の引用符は文字どおり取られます。 SQL_ATTR_METADATA_IDステートメント属性が SQL_FALSE に設定されている場合、これらの引数は通常の引数として扱われます。この属性が SQL_TRUE に設定されている場合、識別子引数として扱われます。  
  
 通常の引数が NULL ポインターに設定され、引数が必須引数である場合、関数は SQL_ERROR および SQLSTATE HY009 (ヌル・ポインターの無効な使用) を戻します。 通常の引数が null ポインターに設定され、引数が必須引数でない場合、引数の動作はドライバーに依存します。 必要な引数を次の表に示します。  
  
|機能|必須の引数|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*をクリックします**。*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
