---
title: パーティションのマージ (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f09255372478bdb9956b64283c8b94477598239
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702043"
---
# <a name="merging-partitions-xmla"></a>パーティションのマージ (XMLA)
  パーティションの集計デザインと構造が同じである場合は、XML for Analysis (XMLA) の[Mergepartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla)コマンドを使用してパーティションをマージできます。 パーティション管理において、パーティションのマージは重要な操作です。日付によってパーティション分割された履歴データを含むパーティションの場合は特に重要です。  
  
 たとえば、次の 2 つのパーティションを使用する財務キューブがあるとします。  
  
-   1 つのパーティションは現在の年の財務データを表し、パフォーマンスのためにリアルタイム リレーショナル OLAP (ROLAP) ストレージ設定を使用します。  
  
-   もう 1 つのパーティションは過去の年の財務データを格納し、ストレージのために多次元 OLAP (MOLAP) ストレージ設定を使用します。  
  
 2 つのパーティションは異なるストレージ設定を使用しますが、集計デザインは同じものを使用します。 年の終わりに複数年にわたる履歴データについてキューブを処理する代わりに、`MergePartitions` コマンドを使用して、現在の年のパーティションを過去の年のパーティションにマージできます。 こうすれば、多くの時間をかけてキューブを詳細に処理しなくても、集計データを保持できます。  
  
## <a name="specifying-partitions-to-merge"></a>マージするパーティションの指定  
 コマンドを実行すると、 [source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)プロパティで指定されたソースパーティションに格納されている集計データが、ターゲットプロパティで指定された対象パーティションに追加されます。 [](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) `MergePartitions`  
  
> [!NOTE]  
>  
  `Source` プロパティには複数のパーティション オブジェクト参照を含めることができます。 しかし、`Target` プロパティには複数を含めることができません。  
  
 正常にマージするためには、`Source` と `Target` で指定されるパーティションが同じメジャー グループに含まれ、同じ集計デザインを使用する必要があります。 一致しないと、エラーが発生します。  
  
 
  `Source` で指定されたパーティションは、`MergePartitions` コマンドが正常に完了した後に削除されます。  
  
## <a name="examples"></a>例  
  
### <a name="description"></a>[説明]  
 次の例では、 **adventure works DW** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]サンプルデータベースの**adventure works**キューブの**Customer カウント**メジャーグループに含まれるすべてのパーティションを、 **Customers_2004**パーティションにマージします。  
  
### <a name="code"></a>コード  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
