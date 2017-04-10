---
title: "属性リレーションシップの定義 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性 [Analysis Services], リレーションシップ"
  - "リレーションシップ [Analysis Services], 属性"
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 属性リレーションシップの定義
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、属性はディメンションの基本的な要素です。 ディメンションには、属性リレーションシップに基づいて構成される一連の属性が含まれます。  
  
 ディメンションに含まれるテーブルごとに、テーブルのキー属性をそのテーブルの別の属性に関連付ける属性リレーションシップがあります。 このリレーションシップは、ディメンションの作成時に作成します。  
  
 属性リレーションシップには、次の利点があります。  
  
-   ディメンション処理に必要なメモリの量が減少します。 これにより、ディメンション、パーティション、およびクエリの処理速度が上がります。  
  
-   ストレージへのアクセスが高速になり、実行プランがより適切に最適化されるため、クエリ パフォーマンスが向上します。  
  
-   ユーザー定義階層がリレーションシップのパスに沿って定義されている場合、集計デザイン アルゴリズムによってより効果的な集計が選択されます。  
  
    > [!NOTE]  
    >  属性リレーションシップの定義と構成の重要性および影響の詳細については、「[SQL Server 2005 Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/?LinkId=81621)」の「クエリ パフォーマンスの向上」を参照してください。  
  
## 属性リレーションシップに関する注意点  
 基になるデータで属性リレーションシップがサポートされる場合、属性間で一意の属性リレーションシップを定義することも必要です。 一意の属性リレーションシップを定義するには、ディメンション デザイナーの **[属性リレーションシップ]** タブを使用します。  
  
 基になるリレーションシップがある属性には、その関連属性を基準とした一意なキーが必要です。 つまり、基になる属性のメンバーによって、関連属性のメンバーが 1 つだけ識別される必要があります。 たとえば、市区町村 -> 都道府県のリレーションシップを考えてみます。 このリレーションシップでは、基になる属性が市区町村、関連属性が都道府県です。 多対一のリレーションシップの "多" に当たるのが基になる属性で、"一" に当たるのが関連属性です。 基になる属性のキーは、市区町村 + 都道府県です。 詳細については、「[属性リレーションシップの作成、変更、または削除](../../analysis-services/multidimensional-models/create-modify-or-delete-an-attribute-relationship.md)」を参照してください。  
  
 属性リレーションシップのプロパティの詳細については、「[属性リレーションシップのプロパティの構成](../../analysis-services/multidimensional-models/configure-attribute-relationship-properties.md)」を参照してください。  
  
> [!NOTE]  
>  属性リレーションシップを正しく定義しないと、クエリ結果が無効になる場合があります。  
  
## 参照  
 [属性リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  