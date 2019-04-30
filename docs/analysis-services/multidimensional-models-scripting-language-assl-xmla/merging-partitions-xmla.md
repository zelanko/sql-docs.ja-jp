---
title: パーティションのマージ (XMLA) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 419ebd0d67b65213fde7393430aedec14249b2ae
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261638"
---
# <a name="merging-partitions-xmla"></a>パーティションのマージ (XMLA)
  使用して、パーティションをマージするには、同じ集計デザインと構造のパーティションがある場合、 [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) XML for Analysis (XMLA) コマンド。 パーティション管理において、パーティションのマージは重要な操作です。日付によってパーティション分割された履歴データを含むパーティションの場合は特に重要です。  
  
 たとえば、次の 2 つのパーティションを使用する財務キューブがあるとします。  
  
-   1 つのパーティションは現在の年の財務データを表し、パフォーマンスのためにリアルタイム リレーショナル OLAP (ROLAP) ストレージ設定を使用します。  
  
-   もう 1 つのパーティションは過去の年の財務データを格納し、ストレージのために多次元 OLAP (MOLAP) ストレージ設定を使用します。  
  
 2 つのパーティションは異なるストレージ設定を使用しますが、集計デザインは同じものを使用します。 年の終わりに履歴データの年の間で、キューブを処理する代わりに使用する、 **MergePartitions**現在の年を過去の年のパーティションにパーティションをマージするコマンド。 こうすれば、多くの時間をかけてキューブを詳細に処理しなくても、集計データを保持できます。  
  
## <a name="specifying-partitions-to-merge"></a>マージするパーティションの指定  
 ときに、 **MergePartitions**コマンドの実行で指定されたソース パーティションに格納された集計データ、[ソース](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)プロパティで指定された対象パーティションに追加されます、[ターゲット](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)プロパティ。  
  
> [!NOTE]  
>  **ソース**プロパティが 1 つ以上のパーティション オブジェクト参照を含めることができます。 ただし、**ターゲット**プロパティことはできません。  
  
 正常にマージするパーティションの両方で指定された、**ソース**と**ターゲット**同じメジャー グループに含まれる必要があり、同じ集計デザインを使用します。 そうでない場合、エラーが発生します。  
  
 指定されたパーティション、**ソース**後に削除されます、 **MergePartitions**コマンドが正常に完了しました。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 次の例では、内のすべてのパーティションのマージ、 **Customer Counts**のメジャー グループ、 **Adventure Works**キューブ、 **Adventure Works DW**サンプル[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]へのデータベース、 **Customers_2004**パーティション。  
  
### <a name="code"></a>コード  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
