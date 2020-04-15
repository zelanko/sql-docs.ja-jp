---
title: LIKE エスケープ シーケンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 517c21f7b64fa7ceb662af9839a9fed1a1e6eff6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304923"
---
# <a name="like-escape-sequence"></a>LIKE エスケープ シーケンス
ODBC は LIKE 句にエスケープ シーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記では、構文は次のとおりです。  
  
 *ODBC に似るエスケープ*::=  
  
 *ODBC-esc-イニシエータ*エスケープ '*エスケープ文字*' *ODBC-esc-終端文字*  
  
 *エスケープ文字*::=*文字*  
  
 *ODBC-esc-イニシエーター* ::= {  
  
 *ODBC-esc 終止符*::= }  
  
 ドライバーが LIKE エスケープ シーケンスをサポートしているかどうかを判断するには、アプリケーションは、SQL_LIKE_ESCAPE_CLAUSE情報の種類を使用して**SQLGetInfo**を呼び出すことができます。
