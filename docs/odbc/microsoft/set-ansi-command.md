---
title: ANSI コマンドを設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97269642b4147b966fdd71003f5f81ebe7905282
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300912"
---
# <a name="set-ansi-command"></a>SET ANSI コマンド
Visual FoxPro SQL コマンドの = 演算子を使用して、長さが異なる文字列間の比較を行う方法を決定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 (ドライバーの既定値、ビジュアル FoxPro の既定値はオフです)。短い文字列に、長い文字列の長さに等しくするために必要な空白を埋めます。 その後、2 つの文字列が、文字の長さ全体で比較されます。 次の比較を検討してください。  
  
```  
'Tommy' = 'Tom'  
```  
  
 結果は False (.F.) SET ANSI がオンの場合、埋め込み時に 'トム' が 'トム' になり、文字列 'トム' と 'Tommy' が文字と一致しないためです。  
  
 == 演算子は、Visual FoxPro SQL コマンドの比較にこのメソッドを使用します。  
  
 OFF  
 短い文字列にブランクを埋め込まないことを指定します。 短い文字列の終わりに達するまで、2 つの文字列は文字の比較文字です。 次の比較を検討してください。  
  
```  
'Tommy' = 'Tom'  
```  
  
 結果は True (.T.) SET ANSI がオフの場合、比較は'トム' の後で停止するためです。  
  
## <a name="remarks"></a>解説  
 SET ANSI は、SQL ストリング比較の実行時に、2 つのストリングの短い方にブランクが埋め込まれているかどうかを判別します。 SET ANSI は== 演算子には影響しません。== 演算子を使用すると、短い文字列には常に比較のためにブランクが埋め込まれます。  
  
## <a name="string-order"></a>文字列の順序  
 SQL コマンドでは、比較で 2 つの文字列の左から右への順序は無関係です= または == 演算子の一方の側から他方の側に文字列を切り替えても、比較の結果には影響しません。  
  
## <a name="see-also"></a>参照  
 [選択 - SQL コマンド](../../odbc/microsoft/select-sql-command.md)   
 [SET EXACT コマンド](../../odbc/microsoft/set-exact-command.md)
