---
title: Query 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e1c7ebcfa06dcabaac4086e6a697f917682e154f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="query-element-xmla"></a>Query 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  内のクエリが含まれています、[クエリ](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)によって使用されるコレクション、 [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)使用法に基づく最適化中にコマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[クエリ](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DesignAggregations** コマンドは、コマンドの **Query** コレクション内に 1 つ以上の **Queries** 要素を含めることにより、使用法に基づく最適化をサポートしています。 各 **Query** 要素は、最もよく使用するクエリを対象とする集計を定義するためにデザイン プロセスが使用する、目標クエリを表します。 ユーザー独自のクエリを指定することもできますが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスによってクエリ ログに格納されている情報を使用して、最もよく使用されるクエリに関する情報を取得することもできます。  
  
 繰り返しの集計をデザインする場合のみがある、最初に目標クエリを渡す**DesignAggregations**コマンドのため、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスがこれらの目標クエリを保存し、後続中にこれらのクエリを使用**DesignAggregations**コマンド。 反復処理の最初の **DesignAggregations** コマンドで目標クエリを渡した場合、後続の **DesignAggregations** コマンドの **Queries** プロパティに目標クエリが含まれていると、エラーが発生します。  
  
 **Query** 要素には、以下の引数を含むコンマ区切りの値が含まれます。  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *頻度*  
 クエリが以前に実行された回数に対応する重み係数です。 **Query** 要素が新しいクエリを表す場合、 *Frequency* の値はクエリを評価するためにデザイン プロセスによって使用される重み係数を表します。 この値が大きいほど、デザイン プロセスでクエリに対して付けられる重みが増加します。  
  
 *データセット*  
 ディメンション内のどの属性をクエリに含めるかを指定する数値文字列です。 この文字列の文字数は、ディメンション内の属性の数と一致している必要があります。 0 は、その位置にある属性が、指定されたディメンションのクエリに含まれないことを示します。1 は、その位置にある属性が、指定されたディメンションのクエリに含まれることを示します。  
  
 たとえば文字列 "011" は、3 つの属性を持つディメンションを処理するクエリの中に、2 番目と 3 番目の属性が含まれることを示しています。  
  
> [!NOTE]  
>  いくつかの属性は、データセットでの考慮の対象から除外されます。 除外される属性の詳細については、「 [Properties (XMLA)](../../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md)」を参照してください。  
  
 集計デザインを含むメジャー グループ内の各ディメンションは、 *Query* 要素の **Dataset** の値によって表されます。 *Dataset* の値の順序は、メジャー グループに含まれるディメンションの順序と一致している必要があります。  
  
## <a name="see-also"></a>参照  
 [デザインの集計 & #40 です。XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
