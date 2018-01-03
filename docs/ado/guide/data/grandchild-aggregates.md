---
title: "孫の集計 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9bc1b08b652f740c576f96b85d99140913079a8b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="grandchild-aggregates"></a>孫の集計
作成される句 shape コマンドのチャプター列を指定することが、*章エイリアス名*(通常の AS キーワード) です。 形状のどのチャプターの任意の列を識別できます**Recordset**列を含む子を識別する完全修飾名を持つ。 たとえば、親章、chap1、子の章では、chap2 に含まれる場合 amt、amount 列を含む、修飾名 chap1.chap2.amt です。修飾名は、集計関数 (SUM、AVG、MAX、MIN、COUNT、STDEV、またはいずれか) のいずれかの引数として使用できます。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
