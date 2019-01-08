---
title: メンバー プロパティ (MDX) の使用 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7876031fddb74115fd1fe412f4c8a9d9aacdb054
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53216041"
---
# <a name="mdx-member-properties"></a>MDX メンバー プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メンバー プロパティは、各組内の各メンバーに関する基本的な情報を対象とします。 基本的な情報には、メンバー名、親レベル、子の数などが含まれます。 メンバー プロパティは特定レベルのすべてのメンバーで使用できます。 編成の点では、メンバー プロパティは 1 つのディメンション上に格納され、ディメンション別に編成されるデータとして扱われます。  
  
> [!NOTE]
>  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、メンバー プロパティを属性リレーションシップと呼んでいます。 詳細については、「 [属性リレーションシップ](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。  
  
 メンバー プロパティには、 *固有* プロパティと *カスタム*プロパティがあります。  
  
 固有メンバー プロパティ  
 すべてのメンバーで、固有メンバー プロパティ (たとえば書式設定済みのメンバーの値など) がサポートされます。一方、ディメンションやレベルには、追加の固有ディメンション メンバー プロパティや追加の固有レベル メンバー プロパティ (たとえばメンバー ID など) が用意されています。  
  
 詳細については、「[固有メンバー プロパティ (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md)」を参照してください。  
  
 ユーザー定義メンバー プロパティ  
 多くの場合、メンバーには追加のプロパティが関連付けられます。 たとえば、製品レベルには、各製品の SKU、SRP、重さ、および量のプロパティが用意されているかもしれません。 これらのプロパティはメンバーではありませんが、製品レベルのメンバーに関する追加情報を含んでいます。  
  
 詳細については、「[ユーザー定義メンバー プロパティ (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md)」を参照してください。  
  
 固有メンバー プロパティとユーザー定義メンバー プロパティは両方とも、**PROPERTIES** キーワードまたは [Properties](../../../mdx/properties-mdx.md) 関数を使用して取得できます。  
  
## <a name="using-the-properties-keyword"></a>PROPERTIES キーワードの使用  
 **PROPERTIES** キーワードを使用して、特定の軸ディメンションに対して使用するメンバー プロパティを指定します。 次の構文では、MDX **SELECT** ステートメントの `<axis specification>` 句に [PROPERTIES](../../../mdx/mdx-data-manipulation-select.md) キーワードが埋め込まれています。  
  
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
>  `<set>` 値と `<axis_name>` 値の詳細については、「[クエリ軸の内容の指定 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。  
  
 `<dim_props>` 句によって、**PROPERTIES** キーワードを使用したディメンション、レベル、およびメンバー プロパティのクエリが実行可能になります。 `<dim_props>` 句の構文は次のとおりです。  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 `<property>` 構文のブレークダウンは、クエリの対象となるプロパティに応じて変わります。  
  
-   状況に依存する固有メンバー プロパティには、その前にディメンション名またはレベル名を指定する必要があります。 ただし、状況に依存しない固有メンバー プロパティはディメンション名やレベル名で修飾できません。 固有メンバー プロパティでの **PROPERTIES** キーワードの使用方法の詳細については、「[固有メンバー プロパティ (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md)」を参照してください。  
  
-   ユーザー定義メンバー プロパティの前には、そのプロパティが存在しているレベルの名前を指定する必要があります。 ユーザー定義メンバー プロパティでの **PROPERTIES** キーワードの使用方法の詳細については、「[ユーザー定義メンバー プロパティ (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プロパティ値の作成および使用 (MDX)](http://msdn.microsoft.com/library/0cafb269-03c8-4183-b6e9-220f071e4ef2)  
  
  
