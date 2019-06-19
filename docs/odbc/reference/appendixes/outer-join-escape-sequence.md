---
title: 外部結合エスケープ シーケンス |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba08d33efca6fa90531f89bd57a307f42f343ebd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63018366"
---
# <a name="outer-join-escape-sequence"></a>外部結合のエスケープ シーケンス
ODBC では、外部結合のエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Remarks  
 BNF 表記では、構文がとおりです。  
  
 *ODBC の外部の結合のエスケープ*:: =  
  
 *ODBC のイニシエーター esc* oj*外部結合 ODBC esc 終端*  
  
 *外部結合*:: =*テーブル名*[*相関名*] {左&#124;右&#124;完全}  
  
 外部結合 {*テーブル名*[*相関名*] &#124; *外部結合*} ON  
  
 *search-*  
  
 *condition*  
  
 *相関名*:: =*ユーザー定義名*  
  
 *ODBC のイニシエーター esc* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 このステートメントのどの部分がサポートされているかを判断するアプリケーションを呼び出す**SQLGetInfo** SQL_OJ_CAPABILITIES 情報の種類にします。 外部結合の*検索条件*間、指定された結合条件のみを含める必要があります*テーブル名*します。
