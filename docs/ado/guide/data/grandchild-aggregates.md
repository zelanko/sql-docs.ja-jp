---
title: 孫集計 |Microsoft Docs
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
ms.openlocfilehash: ac0b06479b3ad4feedaa63bdac227d028b7a9e09
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925238"
---
# <a name="grandchild-aggregates"></a>孫の集計
Shape コマンドの句で作成されたチャプター列には、*章エイリアス名*(通常は AS キーワードを使用) が指定されている場合があります。 列を含む子を識別する完全修飾名を使用して、整形された**レコードセット**の任意のチャプター内の任意の列を識別できます。 たとえば、親章 chap1 に、amount 列を含む chap2 という子のチャプターが含まれている場合、修飾名は chap1 になります。修飾名は、集計関数 (SUM、AVG、MAX、MIN、COUNT、STDEV、ANY) のいずれかの引数として使用できます。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
