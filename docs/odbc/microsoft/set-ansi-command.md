---
title: "SET ANSI コマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d234ae95815df1aae95f3d54781464a752c5fd99
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="set-ansi-command"></a>SET ANSI コマンド
異なる長さの文字列間の比較を実行する方法を決定する、Visual FoxPro SQL コマンド内の演算子を = です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 (ドライバーの既定値以外の場合は Visual FoxPro の既定値は OFF です。)パッド、短い文字列、空白が必要になります。 が長いほどのと同じ文字列の長さです。 2 つの文字列は、その全体の長さの文字の比較対象の文字です。 この比較を考慮してください。  
  
```  
'Tommy' = 'Tom'  
```  
  
 結果は False (です。F.) する場合、ANSI の設定が有効になって埋められる場合は、'Tom' 'Tom' になり、文字列 'Tom' と 'Tommy' は文字を文字に一致しないためです。  
  
 演算子の使用の Visual FoxPro SQL コマンドで比較する場合は、このメソッドを = = です。  
  
 OFF  
 短い文字列を空白で埋めいないことを指定します。 2 つの文字列の比較は短いほうの文字列の末尾に到達するまでの文字の文字です。 この比較を考慮してください。  
  
```  
'Tommy' = 'Tom'  
```  
  
 結果は True (です。T.) と ANSI の設定はオフであるため、比較は、'Tom' の後に停止します。  
  
## <a name="remarks"></a>解説  
 ANSI の設定は、かどうか 2 つの文字列のうち短い方が空白で埋められます SQL 文字列の比較が行われたときを判断します。 ANSI の設定も何も起こりません、= = 演算子使用すると、演算子、= = 短い文字列が比較に空白が埋め込まれた常にします。  
  
## <a name="string-order"></a>文字列の順序  
 SQL コマンドで、左から右の順序比較では 2 つの文字列は irrelevantswitching = の一方の側から文字列 = = または演算子を他の比較の結果に影響はありません。  
  
## <a name="see-also"></a>参照  
 [SQL コマンドを選択します。](../../odbc/microsoft/select-sql-command.md)   
 [SET EXACT コマンド](../../odbc/microsoft/set-exact-command.md)
