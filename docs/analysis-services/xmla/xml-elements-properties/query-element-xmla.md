---
title: "Query 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Query Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords:
- Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b3b6b989932fcb37fba1c137c30658238a0c05df
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="query-element-xmla"></a>Query 要素 (XMLA)
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
 **DesignAggregations** コマンドは、コマンドの **Query** コレクション内に 1 つ以上の **Queries** 要素を含めることにより、使用法に基づく最適化をサポートしています。 各 **Query** 要素は、最もよく使用するクエリを対象とする集計を定義するためにデザイン プロセスが使用する、目標クエリを表します。 独自の目標クエリを指定するかのインスタンスで格納されている情報を使用することができます[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]に関する、最も頻繁に情報を取得するクエリ ログ内のクエリを使用します。  
  
 繰り返しの集計をデザインする場合のみがある、最初に目標クエリを渡す**DesignAggregations**コマンドのため、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスがこれらの目標クエリを保存し、後続中にこれらのクエリを使用**DesignAggregations**コマンド。 反復処理の最初の **DesignAggregations** コマンドで目標クエリを渡した場合、後続の **DesignAggregations** コマンドの **Queries** プロパティに目標クエリが含まれていると、エラーが発生します。  
  
 **Query** 要素には、以下の引数を含むコンマ区切りの値が含まれます。  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *頻度*  
 クエリが以前に実行された回数に対応する重み係数です。 **Query** 要素が新しいクエリを表す場合、 *Frequency* の値はクエリを評価するためにデザイン プロセスによって使用される重み係数を表します。 この値が大きいほど、デザイン プロセスでクエリに対して付けられる重みが増加します。  
  
 *データセット*  
 ディメンション内のどの属性をクエリに含めるかを指定する数値文字列です。 この文字列の文字数は、ディメンション内の属性の数と一致している必要があります。 0 は、その位置にある属性が、指定されたディメンションのクエリに含まれないことを示します。1 は、その位置にある属性が、指定されたディメンションのクエリに含まれることを示します。  
  
 たとえば文字列 "011" は、3 つの属性を持つディメンションを処理するクエリの中に、2 番目と 3 番目の属性が含まれることを示しています。  
  
> [!NOTE]  
>  いくつかの属性は、データセットでの考慮の対象から除外されます。 除外される属性の詳細については、次を参照してください。[プロパティ (XMLA)](../../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md)です。  
  
 集計デザインを含むメジャー グループ内の各ディメンションは、 *Query* 要素の **Dataset** の値によって表されます。 *Dataset* の値の順序は、メジャー グループに含まれるディメンションの順序と一致している必要があります。  
  
## <a name="see-also"></a>参照  
 [デザインの集計 & #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

