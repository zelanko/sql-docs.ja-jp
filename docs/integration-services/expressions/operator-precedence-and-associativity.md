---
title: 演算子の優先順位と結合規則 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9526586f232f31d7c178a6afe5be9ef810eea88b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="operator-precedence-and-associativity"></a>演算子の優先順位と結合規則
  式エバリュエーターがサポートする演算子セット内の各演算子には、優先順位の階層内で指定された優先順位があり、演算子が評価される方向が含まれています。 演算子の評価の方向は、演算子の結合規則と呼ばれます。 優先順位の高い演算子が先に評価されます。 複合式に複数の演算子がある場合、演算子の優先順位により、操作が実行される順序が決定されます。 実行される順序により、結果の値は大きく変わります。 演算子の一部には、優先順位が同じものがあります。 式に複数の演算子が含まれており、その優先順位が同じ場合、それらの演算子は、左から右または右から左の方向に評価されます。  
  
 次の表に、演算子の優先順位が高い順に一覧表示します。 同じレベルの演算子の優先順位は、同じです。  
  
|演算子記号|演算の種類|結合規則|  
|---------------------|-----------------------|-------------------|  
|( )|式|左から右|  
|–、!、~|単項演算子|右から左|  
|キャスト|単項演算子|右から左|  
|*、/、%|乗算|左から右|  
|+、–|加法|左から右|  
|\<、>、\<=、>=|リレーショナル|左から右|  
|==、!=|等式|左から右|  
|&|ビット演算子 AND|左から右|  
|^|ビット演算子排他的 OR|左から右|  
|&#124;|ビット演算子包含的 OR|左から右|  
|&&|論理積|左から右|  
|&#124;&#124;|論理和|左から右|  
|? によってデコードされる文字を次に示します。|条件式|右から左|  
  
## <a name="see-also"></a>参照  
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
