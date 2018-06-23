---
title: Query 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Query Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords:
- Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e01c14cb889a7d2953c98d8dfeee3bb89eee344e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083710"
---
# <a name="query-element-xmla"></a>Query 要素 (XMLA)
  内のクエリが含まれています、[クエリ](queries-element-xmla.md)によって使用されるコレクション、 [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)使用法に基づく最適化中にコマンド。  
  
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[クエリ](queries-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DesignAggregations` コマンドは、コマンドの `Query` コレクション内に 1 つ以上の `Queries` 要素を含めることにより、使用法に基づく最適化をサポートしています。 各`Query`要素は、デザイン プロセスを使用して、最も頻繁に使用するクエリを対象とする集計を定義する、目標クエリを表します。 独自の目標クエリを指定するかのインスタンスで格納されている情報を使用することができます[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]に関する、最も頻繁に情報を取得するクエリ ログ内のクエリを使用します。  
  
 繰り返しの集計をデザインする場合のみがある、最初に目標クエリを渡す`DesignAggregations`コマンドのため、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスがこれらの目標クエリを保存し、後続の中にこれらのクエリを使用`DesignAggregations`コマンド。 反復処理の最初の `DesignAggregations` コマンドで目標クエリを渡した場合、後続の `DesignAggregations` コマンドの `Queries` プロパティに目標クエリが含まれていると、エラーが発生します。  
  
 `Query` 要素には、以下の引数を含むコンマ区切りの値が含まれます。  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *頻度*  
 クエリが以前に実行された回数に対応する重み係数です。 場合、`Query`要素は、新しいクエリを表す、*頻度*値は、クエリを評価するデザイン プロセスによって使用される重み係数を表します。 この値が大きいほど、デザイン プロセスでクエリに対して付けられる重みが増加します。  
  
 *データセット*  
 ディメンション内のどの属性をクエリに含めるかを指定する数値文字列です。 この文字列の文字数は、ディメンション内の属性の数と一致している必要があります。 0 は、その位置にある属性が、指定されたディメンションのクエリに含まれないことを示します。1 は、その位置にある属性が、指定されたディメンションのクエリに含まれることを示します。  
  
 たとえば文字列 "011" は、3 つの属性を持つディメンションを処理するクエリの中に、2 番目と 3 番目の属性が含まれることを示しています。  
  
> [!NOTE]  
>  いくつかの属性は、データセットでの考慮の対象から除外されます。 除外される属性の詳細については、次を参照してください。[プロパティ (XMLA)](query-element-xmla.md)です。  
  
 集計デザインを含むメジャー グループ内の各ディメンションがによって表される、*データセット*値で、`Query`要素。 *Dataset* の値の順序は、メジャー グループに含まれるディメンションの順序と一致している必要があります。  
  
## <a name="see-also"></a>参照  
 [集計のデザイン&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  