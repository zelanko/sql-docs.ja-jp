---
title: 外部結合エスケープ シーケンス |Microsoft ドキュメント
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
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af6a98b3e1a7848fa242dfceb890c472e1d16f74
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
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
