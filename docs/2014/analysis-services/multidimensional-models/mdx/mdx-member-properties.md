---
title: メンバープロパティの使用 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b7fdf989fc23ea70be7d7863f5d4c6ac0b61d8a
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546324"
---
# <a name="using-member-properties-mdx"></a>メンバー プロパティの使用 (MDX)
  メンバー プロパティは、各組内の各メンバーに関する基本的な情報を対象とします。 基本的な情報には、メンバー名、親レベル、子の数などが含まれます。 メンバー プロパティは特定レベルのすべてのメンバーで使用できます。 編成の点では、メンバー プロパティは 1 つのディメンション上に格納され、ディメンション別に編成されるデータとして扱われます。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、メンバー プロパティを属性リレーションシップと呼んでいます。 詳細については、「 [属性リレーションシップ](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。  
  
 メンバー プロパティには、 *固有* プロパティと *カスタム*プロパティがあります。  
  
 固有メンバー プロパティ  
 すべてのメンバーで、固有メンバー プロパティ (たとえば書式設定済みのメンバーの値など) がサポートされます。一方、ディメンションやレベルには、追加の固有ディメンション メンバー プロパティや追加の固有レベル メンバー プロパティ (たとえばメンバー ID など) が用意されています。  
  
 詳細については、「[固有メンバー プロパティ (MDX)](mdx-member-properties-intrinsic-member-properties.md)」を参照してください。  
  
 ユーザー定義メンバー プロパティ  
 多くの場合、メンバーには追加のプロパティが関連付けられます。 たとえば、製品レベルには、各製品の SKU、SRP、重さ、および量のプロパティが用意されているかもしれません。 これらのプロパティはメンバーではありませんが、製品レベルのメンバーに関する追加情報を含んでいます。  
  
 詳細については、「[ユーザー定義メンバー プロパティ (MDX)](mdx-member-properties-user-defined-member-properties.md)」を参照してください。  
  
 `PROPERTIES`キーワードまたは[properties](/sql/mdx/properties-mdx)関数を使用すると、組み込みメンバープロパティとユーザー定義メンバープロパティの両方を取得できます。  
  
## <a name="using-the-properties-keyword"></a>PROPERTIES キーワードの使用  
 `PROPERTIES` キーワードを使用して、特定の軸ディメンションに対して使用するメンバー プロパティを指定します。 キーワードは、 `PROPERTIES` `<axis specification>` MDX の[SELECT](/sql/mdx/mdx-data-manipulation-select)ステートメントの句の中に埋め込まれています。  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 `<axis_specification>` 句には、以下の構文に示すように、オプションの `<dim_props>` 句が含まれています。  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  `<set>` 値と `<axis_name>` 値の詳細については、「[クエリ軸の内容の指定 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。  
  
 `<dim_props>` 句によって、`PROPERTIES` キーワードを使用したディメンション、レベル、およびメンバー プロパティのクエリが実行可能になります。 `<dim_props>` 句の構文は次のとおりです。  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 `<property>` 構文のブレークダウンは、クエリの対象となるプロパティに応じて変わります。  
  
-   状況に依存する固有メンバー プロパティには、その前にディメンション名またはレベル名を指定する必要があります。 ただし、状況に依存しない固有メンバー プロパティはディメンション名やレベル名で修飾できません。 固有メンバープロパティでキーワードを使用する方法の詳細については `PROPERTIES` 、「 [MDX&#41;&#40;固有メンバープロパティ](mdx-member-properties-intrinsic-member-properties.md)」を参照してください。  
  
-   ユーザー定義メンバー プロパティの前には、そのプロパティが存在しているレベルの名前を指定する必要があります。 ユーザー定義メンバープロパティでキーワードを使用する方法の詳細については `PROPERTIES` 、「[ユーザー定義メンバープロパティ &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プロパティ値の作成および使用 (MDX)](../../creating-and-using-property-values-mdx.md)  
  
  
