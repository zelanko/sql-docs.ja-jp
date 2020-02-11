---
title: ハイブリッドコマンド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- hybrid commands [ADO]
- data shaping [ADO], hybrid commands
ms.assetid: e8ca40e8-459c-40e2-8dd3-3ec6d5ee7b51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 486b76708354d4caf7e9efb2f73539b3eea9abf6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925037"
---
# <a name="hybrid-commands"></a>ハイブリッド コマンド
ハイブリッドコマンドは、部分的にパラメーター化されたコマンドです。 次に例を示します。  
  
```  
SHAPE {select * from plants}   
   APPEND( {select * from customers where country = ?}   
           RELATE PlantCountry TO PARAMETER 0,   
             PlantRegion TO CustomerRegion )   
```  
  
 ハイブリッドコマンドのキャッシュ動作は、通常のパラメーター化コマンドと同じです。  
  
## <a name="see-also"></a>参照  
 [データシェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [仮形の文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
