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
manager: jroth
ms.openlocfilehash: e81a2d2274d557bf722a3762f7a3e039dfcc5d4d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700837"
---
# <a name="grandchild-aggregates"></a>孫の集計
Shape コマンドの句の作成」の章の列を指定できます、*章エイリアス名*(通常、AS キーワード) を使用します。 形状の任意の章の任意の列を識別する**レコード セット**列を含む子を識別する完全修飾名。 たとえば、親章、chap1、子の章では、chap2 に含まれる場合 amt、amount 列を持つ、chap1.chap2.amt が修飾名になります。修飾名は、集計関数 (SUM、AVG、MAX、MIN、COUNT、STDEV、またはいずれか) のいずれかの引数として使用できます。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
