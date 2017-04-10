---
title: "メジャーのプロパティの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
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
  - "加法 [Analysis Services]"
  - "ID プロパティ"
  - "ErrorConfiguration プロパティ"
  - "AggregateFunction プロパティ"
  - "DisplayFolder プロパティ"
  - "IgnoreUnrelatedDimensions プロパティ"
  - "FormatString プロパティ"
  - "Description プロパティ"
  - "準加法"
  - "プロパティ [Analysis Services], メジャー グループ"
  - "集計関数 [Analysis Services]"
  - "DataType プロパティ"
  - "ProcessingMode プロパティ"
  - "MeasureExpression プロパティ"
  - "AggregationPrefix プロパティ"
  - "Visible プロパティ"
  - "プロパティ [Analysis Services], メジャー"
  - "StorageLocation プロパティ"
  - "StorageMode プロパティ"
  - "形式 [Analysis Services], メジャー"
  - "Source プロパティ"
  - "集計 [Analysis Services], メジャー"
  - "属性 [Analysis Services], プロパティ"
  - "非加法 [Analysis Services]"
  - "Name プロパティ"
  - "メジャー [Analysis Services], 表示形式"
  - "ProcessingPriority プロパティ"
  - "メジャー グループ [Analysis Services], プロパティ"
  - "Type プロパティ"
  - "ProactiveCaching プロパティ"
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
caps.latest.revision: 50
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 50
---
# メジャーのプロパティの構成
  メジャーには、メジャーの動作を定義し、メジャーがユーザーに表示される方法を制御できるプロパティがあります。  
  
 キューブまたはメジャーを作成または編集する際、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でプロパティを設定できます。 また、MDX または AMO を使用してプログラムで設定することもできます。 詳細については、「[多次元モデル内のメジャーおよびメジャー グループの作成](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)」、「[CREATE MEMBER ステートメント &#40;MDX&#41;](../Topic/CREATE%20MEMBER%20Statement%20\(MDX\).md)」、または「[AMO OLAP 基本オブジェクトのプログラミング](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md)」を参照してください。  
  
## メジャーのプロパティ  
 プロパティがメジャー レベルで上書きされない限り、メジャーはメンバーになっているメジャー グループから特定のプロパティを継承します。 メジャーのプロパティは、メジャーの集計方法、データ型、表示名、メジャーの表示フォルダー、書式設定文字列、メジャーの式、基になるソース列、およびユーザーに対する表示や非表示を決定します。  
  
|プロパティ|定義|  
|--------------|----------------|  
|**AggregateFunction**|必須。 メジャーの集計方法を決定します。 **Sum** は既定の集計です。 各関数の詳しい説明については、「[集計関数の使用](../../analysis-services/multidimensional-models/use-aggregate-functions.md)」を参照してください。|  
|**DataType**|必須。 メジャーのバインド先である、基になるファクト テーブル列のデータ型を指定します。 既定では、この値は基になる列から継承されます。|  
|**Description**|メジャーの説明を指定します。クライアント アプリケーションに表示される場合があります。|  
|**DisplayFolder**|ユーザーがキューブに接続するとメジャーが表示されるフォルダーです。 キューブに多くのメジャーがある場合、表示フォルダーを使用すると、メジャーを分類して表示を見やすく改善できます。|  
|**FormatString**|メジャーの **FormatString** プロパティを使用すると、メジャー値の表示に使用する形式を選択できます。<br /><br /> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] に表示形式の一覧が用意されていますが、一覧にはない追加形式を複数指定できます。 Microsoft Visual Basic で有効な名前付き形式またはユーザー定義形式を指定できます。|  
|**ID**|必須。 メジャーの一意識別子 (ID) です。 このプロパティは読み取り専用です。|  
|**MeasureExpression**|メジャーの値を定義する、制約付きの MDX 式を指定します。 式は、集計前にリーフ レベルで評価され、値の重み付けができるようになります。 たとえば、売上高が為替レートで重み付けされる通貨の換算などです。|  
|**名前**|必須。 メジャーの名前を指定します。|  
|**ソース**|必須。 メジャーがバインドされるデータ ソース ビューの列を指定します。 詳細については、「[データ ソースとバインド &#40;SSAS 多次元&#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)」を参照してください。|  
|**[表示]**|クライアント アプリケーションでメジャーの表示/非表示を決定します。|  
  
## 参照  
 [メジャー グループのプロパティの構成](../../analysis-services/multidimensional-models/configure-measure-group-properties.md)   
 [メジャーの変更](../../analysis-services/modifying-measures.md)  
  
  