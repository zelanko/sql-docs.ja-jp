---
title: "演算子の優先順位と結合規則 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1b6f1c3252fb8a2f68fae20a67cc6174ea41924a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

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
|\<, >, \<=, >=|リレーショナル|左から右|  
|==、!=|等式|左から右|  
|&|ビット演算子 AND|左から右|  
|^|ビット演算子排他的 OR|左から右|  
|&#124;|ビット演算子包含的 OR|左から右|  
|&&|論理積|左から右|  
|&#124;&#124;|論理和|左から右|  
|? [ ] :|条件式|右から左|  
  
## <a name="see-also"></a>参照  
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

