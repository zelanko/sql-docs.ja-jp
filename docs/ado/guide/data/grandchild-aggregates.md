---
title: 孫の集計 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1bff3c8a155e1e9378acbb659f00817f478382e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161606"
---
# <a name="grandchild-aggregates"></a>孫の集計
Shape コマンドの句の作成」の章の列を指定できます、*章エイリアス名*(通常、AS キーワード) を使用します。 形状の任意の章の任意の列を識別する**レコード セット**列を含む子を識別する完全修飾名。 たとえば、親章、chap1、子の章では、chap2 に含まれる場合 amt、amount 列を持つ、chap1.chap2.amt が修飾名になります。修飾名は、集計関数 (SUM、AVG、MAX、MIN、COUNT、STDEV、またはいずれか) のいずれかの引数として使用できます。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
