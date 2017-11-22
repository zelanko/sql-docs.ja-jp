---
title: "論理式 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- logical operators [SQL Server], XQuery
- effective Boolean value [XQuery]
- logical expressions [XQuery]
- EBV
- expressions [XQuery], logical
ms.assetid: de94cd2e-2d48-49fb-9ebd-a2d90c79bf62
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bae1ef29d94019aca590be5d59e72ac4d90910eb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="logical-expressions-xquery"></a>論理式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery をサポートしている論理**と**と**または**演算子。  
  
```  
expression1 and expression2  
expression1 or expression2  
```  
  
 テスト式では、`expression1,``expression2`の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]空のシーケンス、1 つまたは複数のノードのシーケンスまたは単一のブール値になります。 結果に基づいて、次の方法で有効なブール値が決まります。  
  
-   テスト式の結果が空のシーケンスになった場合、式の結果は False になります。  
  
-   テスト式の結果が 1 つのブール値になった場合、この値が式の結果になります。  
  
-   テスト式の結果が 1 つ以上のノードのシーケンスになった場合、式の結果は True になります。  
  
-   それ以外の場合は、静的エラーが発生します。  
  
 論理**と**と**または**演算子は、標準の論理セマンティクスで、式の結果のブール値に適用し、します。  
  
 次のクエリは、特定の製品モデルについて、正面からの小さな写真である <`Picture`> 要素を製品カタログから取得します。 製品の説明ドキュメントごとに、サイズや角度など、異なる属性を持つ 1 つ以上の製品写真をカタログに格納できることに注意してください。  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $F in /PD:ProductDescription/PD:Picture[PD:Size="small"   
                                                 and PD:Angle="front"]  
     return   
         $F   
    ') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 結果を次に示します。  
  
```  
<PD:Picture   
  xmlns:PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  <PD:Angle>front</PD:Angle>  
  <PD:Size>small</PD:Size>  
  <PD:ProductPhotoID>31</PD:ProductPhotoID>  
</PD:Picture>  
  
```  
  
## <a name="see-also"></a>参照  
 [XQuery 式](../xquery/xquery-expressions.md)  
  
  
