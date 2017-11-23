---
title: "外部結合エスケープ シーケンス |Microsoft ドキュメント"
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
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 947a3ad16efa1b34176311b6ad70b36635dda6f6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
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
  
 *外部結合*:: =*テーブル名*[*相関名*] {左 &#124;です。右 &#124;です。完全}  
  
 OUTER JOIN {*テーブル名*[*相関名*] &#124;です。*外部結合*} ON  
  
 *検索-*  
  
 *条件*  
  
 *相関名*:: =*ユーザー定義名*  
  
 *ODBC esc イニシエーター* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 アプリケーションが呼び出す調べるには、このステートメントのどの部分がサポートされている、 **SQLGetInfo** SQL_OJ_CAPABILITIES 情報の種類とします。 外部結合の*検索条件*間、指定された結合条件のみを含める必要があります*テーブル名*です。
