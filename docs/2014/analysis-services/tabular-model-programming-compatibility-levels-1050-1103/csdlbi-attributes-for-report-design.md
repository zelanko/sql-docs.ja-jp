---
title: レポート デザインの CSDLBI 属性 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 61ba3a27-790e-43bc-b421-e01bf2fdbda6
caps.latest.revision: 8
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e9d68293f4f71280c09d43a6b60dfa087830dc4d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083066"
---
# <a name="csdlbi-attributes-for-report-design"></a>レポート デザインの CSDLBI 属性
  このセクションでは、テーブル モデリングについての CSDL に対する拡張機能の、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] クエリ デザインに影響のある属性について説明します。  
  
## <a name="model-attributes"></a>モデル属性  
 これらの属性が、CSDL のサブ要素で定義されている[EntityContainer](http://msdn.microsoft.com/library/bb399169.aspx)要素。  
  
|属性名|データ型|説明|  
|--------------------|---------------|-----------------|  
|カルチャ|Text|通貨形式に使用されるカルチャを示します。 省略した場合は、EN-US が使用されます。|  
|IsRightToLeft|ブール値|テキスト フィールドの値を既定で右から左に読む必要があるかどうかを示します。|  
  
## <a name="entity-attributes"></a>エンティティ属性  
 以下の属性は、CSDL の EntitySet または EntityType 要素のサブ要素で定義されています。  
  
|属性名|データ型|説明|  
|--------------------|---------------|-----------------|  
|`ReferenceName`|Text|DAX クエリでこのエンティティを参照するために使用される識別子。 省略した場合は、名前が使用されます。|  
|`Caption`|Text|エンティティの表示名。|  
|`Documentation`|Text|ビジネス ユーザーがデータの意味を理解できるように説明するテキスト。|  
|`Hidden`|ブール値|エンティティを表示するかどうかを示します。 既定値は `false` です。|  
|`CollectionCaption`|Text|エンティティのインスタンスのセットを参照するための複数形の名前。 省略した場合は、Caption 属性が使用されます。|  
|`DisplayKey`|MemberRef[]|ビジネス ユーザーに対してエンティティのインスタンスを示すために使用されるフィールドの順序付きリスト。 参照には、インスタンス プロパティとナビゲーション プロパティを含めることができます。 ナビゲーションプロパティが参照されている場合は、ターゲット エンティティの `DisplayKey` が表示されます 。 `DisplayKey` の値を指定しないと、キー フィールドが使用されます。|  
|`DefaultImage`|MemberRef|ビジネス ユーザーに対してエンティティのインスタンスを視覚的に示すために使用される画像を含むフィールドの参照。 省略した場合は、エンティティの最初の画像フィールドが使用されます (存在する場合)。|  
|`DefaultDetails`|MemberRef[]|ビジネス ユーザーに対して表示されるエンティティ インスタンスについての詳細情報の既定セットを表すフィールドの順序付きリスト。省略すると、エンティティの最初の 5 つのフィールドが使用されます。ただし、`Key`、`DisplayKey`、または `DefaultImage` によって既に参照されているフィールドは除外されます。|  
|`SortProperties`|MemberRef[]|エンティティ インスタンスの標準的な並べ替えに使用されるフィールドの順序付きリスト。 これらのフィールドで並べ替えられるときは、各フィールドで指定されている `SortDirection` が使用されます。 省略した場合は、`DisplayKey` フィールドが使用されます。|  
|`DefaultMeasure`|MemberRef|メジャーまたはフィールドをエンティティの複数のインスタンスに対する既定の表現として使用する必要があることを示すための、モデルで定義されているメジャー、または既定の集計関数のある数値フィールドの参照。 省略した場合は、エンティティ インスタンスの数が使用されます。|  
|`DefaultLocation`|MemberRef|値がエンティティ インスタンスと関連付けられた既定の場所を表しているフィールドの参照。 省略した場合は、エンティティの最初の場所フィールドが使用されます (存在する場合)。|  
  
## <a name="field-attributes"></a>フィールドを属性します。  
 これらの属性は CSDL Property のサブ要素で定義されているまたは[NavigationProperty](http://msdn.microsoft.com/library/bb387104.aspx)要素。  
  
|属性名|データ型|説明|  
|--------------------|---------------|-----------------|  
|`ReferenceName`|Text|DAX クエリでこのエンティティを参照するために使用される識別子。 省略した場合は、フィールド名が使用されます。|  
|`Caption`|Text|エンティティの表示名。 省略した場合は、フィールドの `ReferenceName` が使用されます。|  
|`Documentation`|Text|ビジネス ユーザーがフィールドの意味を理解できるように説明するテキスト。|  
|`Hidden`|ブール値|フィールドを表示するかどうかを示します。 既定値は `false` で、フィールドが表示されることを意味します。|  
|`DisplayFolder`|Text|このフィールドが表示されるフォルダーの名前 (完全なパス)。 省略した場合、フィールドはモデルのルートに表示されます。|  
|`ContextualNameRule`|Enum|プロパティ名をそれが使用されるコンテキストに基づいて変更する必要があるかどうか、および変更する方法を示す値。 指定できる値は: `None`、 `Role`、`Merge`です。|  
|`Alignment`|Enum|表形式の表示でフィールドの値を配置する方法を示す値。 指定できる値は、`Default`、`Center`、`Left`、`Right` です。 省略した場合は、フィールドのデータ型に基づいて既定の配置が決定されます。|  
|`FormatString`|Text|フィールドの値の既定での書式設定方法を示す .NET 形式の文字列。 省略した場合は、次の形式と見なされます。<br /><br /> -Datetime フィールド: 地域の短い日付または"d"<br />-集計関数を浮動小数点フィールドと、既定値である整数フィールド: 地域の数値または"n"<br />-集計関数を既定値はありません整数: 地域の 10 進数または"d"<br /><br /> 他のすべての型のフィールドについては、書式指定文字列は適用されません。|  
|`Units`|Text|単位を表現するためにフィールド値に適用される記号。 省略した場合、単位は不明と見なされます。|  
|`Width`|Integer|表形式の表示でフィールドの値を表示するために確保する必要のある望ましい幅 (文字数)。 省略した場合は、フィールドのデータ型に基づいて既定の幅が決定されます。|  
|`SortDirection`|Enum|フィールドの値が通常並べ替え方法を示す値。 指定できる値は、`Default`、`Ascending`、`Descending` です。 省略した場合は、フィールドのデータ型に基づいて既定の並べ替え方向が決定されます。|  
|`IsRightToLeft`|ブール値|右から左に読む必要のあるテキストがフィールドに含まれるかどうかを示します。 省略した場合は、モデルの設定と見なされます。|  
|`OrderBy`|MemberRef|このフィールドの値の並べ替え順序が定義されているモデル内の別のフィールドの参照。 2 つのフィールドの値は 1:1 で対応している必要があります。そうでない場合、並べ替えの動作は定義されません。 省略した場合、フィールドはそれ自体の値に基づいて並べ替えられます。|  
|`Contents`|Enum|フィールドのサブタイプまたは内容を記述する列挙。 省略した場合、特定のサブタイプは想定されません。ただし、フィールドのデータ型が Binary の場合は、Image と想定されます。 サポートされるコンテンツ タイプの詳細については、AMO のドキュメントを参照してください。|  
|`DefaultAggregateFunction`|Enum|このフィールドの集計に通常使用される既定の関数を示す値 (ある場合)。 使用できる値は、`None`、`Sum`、`Average`、`Count`、`Min`、`Max` です。 省略した場合、数値フィールドについては `Sum` と想定され、他のすべてのフィールドについては `None` と想定されます。|  
|`IsSimpleMeasure`|ブール値|メジャーが単に数値フィールドの単純な集計かどうかを示します。 このような集計はクエリで必要に応じて簡単に定義できるので、パフォーマンス向上のためモデル定義では省略する必要があります。 省略した場合は、`false` と想定されます。|  
|`Kpi`<br /><br /> `KpiGoal`<br /><br /> `KpiStatus`|サブ要素|メジャー要素が KPI として使用されることを示します。 KPI サブ要素では、KpiGoal および KpiStauts 要素を使用して、関連する表示画像とターゲット範囲が定義されます。|  
  
  