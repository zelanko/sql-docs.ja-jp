---
title: 属性リレーションシップ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9464354539cb3da93314d7e986faa54acae2029
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-relationships"></a>のディメンション デザイナーでは、[ディメンション構造] ビューの
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]属性、ディメンション内で常に関連している直接的または間接的にキー属性にします。 同一のリレーショナル テーブルからすべてのディメンション属性が派生するスター スキーマに基づいてディメンションを定義すると、ディメンションのキー属性と各非キー属性の間に自動的に属性リレーションシップが定義されます。 関連を持った複数のテーブルからディメンション属性が派生するスノーフレーク スキーマを基にディメンションを定義すると、属性リレーションシップが自動的に次のように定義されます。  
  
-   キー属性と、メイン ディメンション テーブルの列にバインドされた各非キー属性の間  
  
-   キー属性と、基になるディメンション テーブルにリンクしているセカンダリ テーブルの外部キーにバインドされた属性の間  
  
-   セカンダリ テーブルの外部キーにバインドされた属性と、セカンダリ テーブルの列にバインドされた各非キー属性の間  
  
 ただし、さまざまな理由で、上記の既定の属性リレーションシップの変更が必要になる場合もあります。 たとえば、非キー属性に基づいて、自然階層、カスタムの並べ替え順、ディメンションの粒度などを定義できます。 詳細については、次を参照してください。 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)です。  
  
> [!NOTE]  
>  属性リレーションシップは、多次元式 (MDX) ではメンバーのプロパティと呼ばれます。  
  
## <a name="natural-hierarchy-relationships"></a>自然階層リレーションシップ  
 ユーザー定義階層内の各属性がそのすぐ下の属性と一対多のリレーションシップにある場合、階層は自然階層になります。 たとえば、次の 8 つの列から構成されるリレーショナル ソース テーブルを基にした Customer ディメンションを考えてみます。  
  
-   CustomerKey  
  
-   CustomerName  
  
-   Age  
  
-   Gender  
  
-   EMail  
  
-   City  
  
-   Country  
  
-   Region  
  
 対応する Analysis Services ディメンションには、次の 7 つの属性があります。  
  
-   Customer (CustomerKey キーを基に CustomerName でメンバー名を指定)  
  
-   Age、Gender、Email、City、Region、Country  
  
 自然階層を表すリレーションシップを適用するには、あるレベルの属性とその下のレベルの属性との間に属性リレーションシップを作成します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、このしくみによって、自然なリレーションシップと潜在的な集計が指定されます。 Customer ディメンションには、Country 属性、Region 属性、City 属性、および Customer 属性に対する自然階層が存在します。 `{Country, Region, City, Customer}` の自然階層は、次の属性リレーションシップを追加して記述します。  
  
-   Region 属性に対する属性リレーションシップとしての Country 属性  
  
-   City 属性に対する属性リレーションシップとしての Region 属性  
  
-   Customer 属性に対する属性リレーションシップとしての City 属性  
  
 キューブ内のデータを移動するため、データの自然階層を表さないユーザー定義の階層を作成することも (と呼ばれる、*アドホック*または*reporting*階層)。 たとえば、`{Age, Gender}` を基にしたユーザー定義階層を作成できます。 自然階層には、ソース データ内の自然なリレーションシップを表した構造をユーザーからは見えないところで集計およびインデックス化する利点がありますが、ユーザーにはこの 2 つの階層の動作の違いはわかりません。  
  
 **SourceAttribute**レベルのプロパティを決定する属性を使用して、レベルを説明します。 **KeyColumns**属性のプロパティでは、メンバーを提供するデータ ソース ビューの列を指定します。 **NameColumn**属性のプロパティは、メンバーの別の名前列を指定できます。  
  
 使用して、ユーザー定義階層のレベルを定義する[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、**ディメンション デザイナー**のデータ ソース ビューに含まれる関連テーブルからディメンション属性、ディメンション テーブル内の列または列を選択することができますキューブです。 ユーザー定義階層の作成の詳細については、次を参照してください。 [Create User-Defined 階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)です。  
  
 Analysis Services では通常、メンバーの内容が想定されています。 リーフ メンバーには子孫がなく、元のデータ ソースから派生したデータが含まれています。 非リーフ メンバーには子孫があり、子メンバーで実行した集計から派生したデータが含まれています。 集計レベルのメンバーは、下位レベルの集計が基になっています。 したがって、ときに、 **IsAggregatable**プロパティに設定されている**False**レベルの基になる属性の集計可能な属性は追加されませんその上のレベルとして。  
  
## <a name="defining-an-attribute-relationship"></a>属性リレーションシップの定義  
 属性リレーションシップを作成するときの主な制約は、属性リレーションシップによって参照される属性に、属性リレーションシップが所属する属性のメンバーの値が 2 つ以上含まれていないことを確認する必要があることです。 たとえば、City 属性と State 属性の間のリレーションシップを定義する場合、それぞれの市区町村は 1 つの都道府県にのみ関連付けることができます。  
  
## <a name="attribute-relationship-queries"></a>属性リレーションシップのクエリ  
 と共にメンバー プロパティの形式で、属性リレーションシップからデータを取得する MDX クエリを使用することができます、**プロパティ**MDX のキーワード**選択**ステートメントです。 MDX を使用して、メンバー プロパティを取得する方法の詳細については、次を参照してください。[メンバー プロパティの使用 & #40 です。MDX と #41 です。](../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [ユーザー階層プロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
