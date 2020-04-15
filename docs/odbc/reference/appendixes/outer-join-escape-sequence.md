---
title: 外部結合エスケープシーケンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37ce446328d263f492cdfd369f6e8f9f64fe6dfc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303613"
---
# <a name="outer-join-escape-sequence"></a>外部結合のエスケープ シーケンス
ODBC では、外部結合にエスケープ シーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記では、構文は次のとおりです。  
  
 *ODBC 外部結合エスケープ*::=  
  
 *ODBC-esc-イニシエーター* oj*外部結合 ODBC-esc-終端文字*  
  
 *外部結合*::=*テーブル名*[*相関名*] {左&#124; RIGHT &#124; FULL}  
  
 OUTER JOIN {*テーブル名*[*相関名*] &#124;*外部結合*} オン  
  
 *検索-*  
  
 *条件*  
  
 *相関名*::=*ユーザー定義名*  
  
 *ODBC-esc-イニシエーター* ::= {  
  
 *ODBC-esc 終止符*::= }  
  
 このステートメントのどの部分がサポートされているかを判別するために、アプリケーションは SQL_OJ_CAPABILITIES情報タイプを指定して**SQLGetInfo**を呼び出します。 外部結合の場合、*検索条件*には、指定された*テーブル名*の間の結合条件のみを含める必要があります。
