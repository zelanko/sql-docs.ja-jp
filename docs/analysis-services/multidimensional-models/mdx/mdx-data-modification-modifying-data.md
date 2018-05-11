---
title: データの変更 (MDX) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 720cf79b92c840fd41ae8453b41fbbe18cefe19f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-data-modification---modifying-data"></a>MDX データ変更のデータの変更
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  多次元式 (MDX) は、ディメンションやキューブのデータの取得や操作を行うためだけでなく、ディメンションやキューブのデータの更新、つまり*書き戻し*を行うためにも使用できます。 これらの更新は、推測分析または "what-if" 分析の場合のように一時的なものであることも、データ分析に基づいて変更を加える必要がある場合のように永続的なものになることもあります。  
  
 データの更新は、ディメンション レベルまたはキューブ レベルで実行できます。  
  
 **ディメンションの書き戻し**  
 書き込み可能なディメンションのデータを変更するには、 [ALTER CUBE ステートメント (MDX)](../../../mdx/mdx-data-definition-alter-cube.md) を使用します。属性値の削除、作成、更新を反映するには、 [REFRESH CUBE ステートメント (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) を使用します。 ALTER CUBE ステートメントを使用すると、階層内のサブツリー全体を削除したり、削除されたメンバーの子を昇格させるなど、複雑な操作を実行することもできます。  
  
 **キューブの書き戻し**  
 書き込み可能なキューブに対する更新を実行するには、 [UPDATE CUBE](../../../mdx/mdx-data-manipulation-update-cube.md) ステートメントを使用します。 UPDATE CUBE ステートメントを使用すると、特定の値で組を更新できます。 サーバーにある更新されたデータをクライアント セッションのデータに適用するには、[REFRESH CUBE ステートメント (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) を使用します。  
  
 詳細については、「[キューブの書き戻しの使用 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-using-cube-writebacks.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [MDX クエリの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
