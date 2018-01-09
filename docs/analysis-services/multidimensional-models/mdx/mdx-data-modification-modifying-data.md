---
title: "データの変更 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fcf75945b77c8ced0321089805f7e23fc7223821
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-modification---modifying-data"></a>MDX データ変更のデータの変更
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]更新に MDX を使用する多次元式 (MDX) を使用して、取得し、ディメンションとキューブからデータを処理するだけでなくまたは*書き戻し*ディメンションとキューブのデータ。 これらの更新は、推測分析または "what-if" 分析の場合のように一時的なものであることも、データ分析に基づいて変更を加える必要がある場合のように永続的なものになることもあります。  
  
 データの更新は、ディメンション レベルまたはキューブ レベルで実行できます。  
  
 **ディメンションの書き戻し**  
 書き込み可能なディメンションのデータを変更するには、 [ALTER CUBE ステートメント (MDX)](../../../mdx/mdx-data-definition-alter-cube.md) を使用します。属性値の削除、作成、更新を反映するには、 [REFRESH CUBE ステートメント (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) を使用します。 ALTER CUBE ステートメントを使用すると、階層内のサブツリー全体を削除したり、削除されたメンバーの子を昇格させるなど、複雑な操作を実行することもできます。  
  
 **キューブの書き戻し**  
 書き込み可能なキューブに対する更新を実行するには、 [UPDATE CUBE](../../../mdx/mdx-data-manipulation-update-cube.md) ステートメントを使用します。 UPDATE CUBE ステートメントを使用すると、特定の値で組を更新できます。 サーバーにある更新されたデータをクライアント セッションのデータに適用するには、[REFRESH CUBE ステートメント (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) を使用します。  
  
 詳細については、「[キューブの書き戻しの使用 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-using-cube-writebacks.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [MDX クエリの基礎 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
