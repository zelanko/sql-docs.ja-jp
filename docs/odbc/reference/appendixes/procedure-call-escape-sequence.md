---
title: "プロシージャ呼び出しのエスケープ シーケンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0ba89ae47d223ea17f02cb07976510d78ff3660e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
