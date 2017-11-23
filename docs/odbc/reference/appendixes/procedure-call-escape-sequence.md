---
title: "プロシージャ呼び出しのエスケープ シーケンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c59924e443d738b1bc3e61092a02e617f0d39eff
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="procedure-call-escape-sequence"></a>プロシージャ呼び出しのエスケープ シーケンス
ODBC では、プロシージャ呼び出しのエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
 **{**[? =]**呼び出す***プロシージャ名*[**(**[*パラメーター*] [、[*パラメーター*]...**)**]**}**  
  
 BNF 表記で、構文のとおりです。  
  
 *ODBC プロシージャ エスケープ*:: =  
  
 &#124; です。*ODBC esc イニシエーター* [? =] 呼び出す*プロシージャ esc 終端の ODBC*  
  
 *プロシージャ*:: =*プロシージャ名*&#124; です。*プロシージャ名*(*プロシージャ パラメーターのリストを*)  
  
 *プロシージャ識別子*:: =*ユーザー定義名*  
  
 *プロシージャ名*:: =*プロシージャ識別子*  
  
 &#124; です。*所有者名*.*プロシージャ識別子*  
  
 &#124; です。*カタログ名のカタログの区切り**プロシージャ識別子*  
  
 &#124; です。*カタログ名のカタログの区切り*[*所有者名*].*プロシージャ識別子*  
  
 (3 番目の構文は、データ ソースは所有者をサポートしていない場合にのみ有効です)。  
  
 *所有者名*:: =*ユーザー定義名*  
  
 *カタログ名*:: =*ユーザー定義名*  
  
 *カタログの区切り*:: = {*実装定義*}  
  
 (カタログの区切り記号がによって返される**SQLGetInfo** SQL_CATALOG_NAME_SEPARATOR 情報オプションを使用します)。  
  
 *プロシージャ パラメーターのリストを*:: =*プロシージャ パラメーター*  
  
 &#124; です。*プロシージャ パラメーター*、*プロシージャ パラメーター リスト*  
  
 *プロシージャ パラメーター* :: =*動的パラメーター* &#124; です。*リテラル*&#124; です。*空文字列*  
  
 *空の文字列*:: =  
  
 *ODBC esc イニシエーター* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 (プロシージャのパラメーターが空の文字列の場合は、プロシージャ、既定値、パラメーターに対して使用します。)  
  
 アプリケーションが呼び出すことができます、データ ソースには、プロシージャがサポートしていて、ドライバーは ODBC のプロシージャの呼び出し構文をサポートするかどうかを調べるに**SQLGetInfo** SQL_PROCEDURES 情報の種類とします。
