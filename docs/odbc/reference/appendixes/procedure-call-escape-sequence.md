---
title: プロシージャコールエスケープシーケンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1194efe6a21c456a722ccd4352661c998f0316d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298222"
---
# <a name="procedure-call-escape-sequence"></a>プロシージャ呼び出しのエスケープ シーケンス
ODBC は、プロシージャ呼び出しにエスケープ シーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
 **{**[?=] プロシージャ*名*を**呼び出す**[**] [***パラメータ*],[*パラメータ*]..**)**]**}**  
  
 BNF 表記では、構文は次のとおりです。  
  
 *ODBC プロシージャ エスケープ*::=  
  
 *&#124; ODBC-esc-イニシエータ*[?=] 呼び出し*プロシージャ ODBC-esc-終端文字*  
  
 *プロシージャ*::=*プロシージャ名*&#124;*プロシージャ名*(*プロシージャ パラメータ リスト*)  
  
 *プロシージャ識別子*::=*ユーザー定義名*  
  
 *プロシージャ名*::=*プロシージャ識別子*  
  
 *所有者名*&#124;。*プロシージャ識別子*  
  
 カタログ*名カタログ区切り文字プロシージャー* *ID を*&#124;  
  
 *カタログ名カタログ区切り記号*[*所有者名*] を&#124;します。*プロシージャ識別子*  
  
 (3 番目の構文は、データ ソースが所有者をサポートしていない場合にのみ有効です)。  
  
 *所有者名*::=*ユーザー定義名*  
  
 *カタログ名*::=*ユーザー定義名*  
  
 *カタログ区切り ::=* {*実装定義*}  
  
 (カタログ区切り記号は、SQL_CATALOG_NAME_SEPARATOR情報オプションを指定して**SQLGetInfo**を介して返されます。  
  
 *プロシージャ-パラメータリスト*::=*プロシージャパラメータ*  
  
 *&#124; プロシージャ パラメータ*, プロシージャ パラメータ*リスト*  
  
 *プロシージャ-パラメータ*::=*動的パラメータ*&#124;*リテラル*&#124;*空文字列*  
  
 *空文字列*::=  
  
 *ODBC-esc-イニシエーター* ::= {  
  
 *ODBC-esc 終止符*::= }  
  
 プロシージャ パラメータが空の文字列の場合、プロシージャはそのパラメータのデフォルト値を使用します。  
  
 データ ソースがプロシージャをサポートし、ドライバーが ODBC プロシージャ呼び出し構文をサポートしているかどうかを判断するには、アプリケーションは、SQL_PROCEDURES情報の種類を使用して**SQLGetInfo**を呼び出すことができます。
