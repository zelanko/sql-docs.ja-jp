---
title: 外部結合エスケープ シーケンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31d7ea1f4a349e2a0207481cb85ab898548bd98d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="outer-join-escape-sequence"></a>外部結合エスケープ シーケンス
ODBC では、外部結合のエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記で、構文のとおりです。  
  
 *ODBC outer で結合のエスケープ*:: =  
  
 *ODBC esc イニシエーター* oj*外部結合 ODBC esc ターミネータ*  
  
 *外部結合*:: =*テーブル名*[*相関名*] {左&#124;右&#124;完全}  
  
 外部結合 {*テーブル名*[*相関名*] &#124; *外部結合*} ON  
  
 *検索-*  
  
 *条件*  
  
 *相関名*:: =*ユーザー定義名*  
  
 *ODBC esc イニシエーター* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 アプリケーションが呼び出す調べるには、このステートメントのどの部分がサポートされている、 **SQLGetInfo** SQL_OJ_CAPABILITIES 情報の種類とします。 外部結合の*検索条件*間、指定された結合条件のみを含める必要があります*テーブル名*です。
