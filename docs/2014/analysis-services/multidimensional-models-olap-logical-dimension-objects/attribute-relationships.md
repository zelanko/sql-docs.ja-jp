---
title: 属性リレーションシップ |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81d51c8778cfbc6e3891dfb3b6783db48f0c65a2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62728518"
---
# <a name="attribute-relationships"></a>のディメンション デザイナーでは、[ディメンション構造] ビューの
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、ディメンション内の属性は常に、直接または間接的にキー属性に関連付けられます。 同一のリレーショナル テーブルからすべてのディメンション属性が派生するスター スキーマに基づいてディメンションを定義すると、ディメンションのキー属性と各非キー属性の間に自動的に属性リレーションシップが定義されます。 関連を持った複数のテーブルからディメンション属性が派生するスノーフレーク スキーマを基にディメンションを定義すると、属性リレーションシップが自動的に次のように定義されます。  
  
-   キー属性と、メイン ディメンション テーブルの列にバインドされた各非キー属性の間  
  
-   キー属性と、基になるディメンション テーブルにリンクしているセカンダリ テーブルの外部キーにバインドされた属性の間  
  
-   セカンダリ テーブルの外部キーにバインドされた属性と、セカンダリ テーブルの列にバインドされた各非キー属性の間  
  
 ただし、さまざまな理由で、上記の既定の属性リレーションシップの変更が必要になる場合もあります。 たとえば、非キー属性に基づいて、自然階層、カスタムの並べ替え順、ディメンションの粒度などを定義できます。 詳細については、「[ディメンション属性プロパティのリファレンス](../multidimensional-models/dimension-attribute-properties-reference.md)」を参照してください。  
  
> [!NOTE]  
>  属性リレーションシップは、多次元式 (MDX) ではメンバーのプロパティと呼ばれます。  
  
## <a name="natural-hierarchy-relationships"></a>自然階層リレーションシップ  
 ユーザー定義階層内の各属性がそのすぐ下の属性と一対多のリレーションシップにある場合、階層は自然階層になります。 たとえば、次の 8 つの列から構成されるリレーショナル ソース テーブルを基にした Customer ディメンションを考えてみます。  
  
-   CustomerKey  
  
-   CustomerName  
  
-   Age  
  
-   性別  
  
-   電子メール  
  
-   City  
  
-   Country  
  
-   リージョン  
  
 対応する Analysis Services ディメンションには、次の 7 つの属性があります。  
  
-   Customer (CustomerKey キーを基に CustomerName でメンバー名を指定)  
  
-   Age、Gender、Email、City、Region、Country  
  
 自然階層を表すリレーションシップを適用するには、あるレベルの属性とその下のレベルの属性との間に属性リレーションシップを作成します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、このしくみによって、自然なリレーションシップと潜在的な集計が指定されます。 Customer ディメンションには、Country 属性、Region 属性、City 属性、および Customer 属性に対する自然階層が存在します。 `{Country, Region, City, Customer}` の自然階層は、次の属性リレーションシップを追加して記述します。  
  
-   Region 属性に対する属性リレーションシップとしての Country 属性  
  
-   City 属性に対する属性リレーションシップとしての Region 属性  
  
-   Customer 属性に対する属性リレーションシップとしての City 属性  
  
 キューブ内のデータを移動する場合は、データの自然階層を表さないユーザー定義階層 (*アドホック*または*レポート*階層と呼ばれます) を作成することもできます。 たとえば、`{Age, Gender}` を基にしたユーザー定義階層を作成できます。 ユーザーは、2つの階層がどのように動作するかに違いはありません。ただし、自然階層は、ソースデータ内の自然なリレーションシップのために、ユーザーから非表示になります。  
  
 あるレベルの `SourceAttribute` プロパティには、そのレベルの記述に使用する属性を指定します。 属性の `KeyColumns` プロパティには、メンバーの取り込み元のデータ ソース ビューの列を指定します。 属性の `NameColumn` プロパティには、別の名前列をメンバーに対して指定できます。  
  
 を使用して[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ユーザー定義階層内のレベルを定義するには、ディメンション**デザイナー**でディメンション属性、ディメンションテーブルの列、またはキューブのデータソースビューに含まれる関連テーブルの列を選択します。 ユーザー定義階層の作成の詳細については、「[ユーザー定義階層の作成](../multidimensional-models/user-defined-hierarchies-create.md)」を参照してください。  
  
 Analysis Services では通常、メンバーの内容が想定されています。 リーフ メンバーには子孫がなく、元のデータ ソースから派生したデータが含まれています。 非リーフ メンバーには子孫があり、子メンバーで実行した集計から派生したデータが含まれています。 集計レベルのメンバーは、下位レベルの集計が基になっています。 したがって、あるレベルのソース属性の `IsAggregatable` プロパティを `False` に設定するときは、集計可能な属性をこれより上位のレベルとして追加しないでください。  
  
## <a name="defining-an-attribute-relationship"></a>属性リレーションシップの定義  
 属性リレーションシップを作成するときの主な制約は、属性リレーションシップによって参照される属性に、属性リレーションシップが所属する属性のメンバーの値が 2 つ以上含まれていないことを確認する必要があることです。 たとえば、City 属性と State 属性の間のリレーションシップを定義する場合、それぞれの市区町村は 1 つの都道府県にのみ関連付けることができます。  
  
## <a name="attribute-relationship-queries"></a>属性リレーションシップのクエリ  
 MDX クエリを使用すると、MDX `PROPERTIES` ステートメントの `SELECT` キーワードを指定することにより、メンバーのプロパティの形式で属性リレーションシップからデータを取得することができます。 MDX を使用してメンバープロパティを取得する方法の詳細については、「 [mdx&#41;&#40;メンバープロパティを使用](../multidimensional-models/mdx/mdx-member-properties.md)する」を参照してください。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](attributes-and-attribute-hierarchies.md)   
 [ディメンションの属性のプロパティのリファレンス](../multidimensional-models/dimension-attribute-properties-reference.md)   
 [ユーザー階層](user-hierarchies.md)   
 [ユーザー階層プロパティ](user-hierarchies-properties.md)  
  
  
