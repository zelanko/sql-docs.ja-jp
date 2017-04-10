---
title: "ユーザー定義階層の追加または削除 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "階層 [Analysis Services], 追加"
  - "階層の除去"
  - "階層の追加"
  - "階層の削除"
  - "階層 [Analysis Services], 削除"
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
caps.latest.revision: 51
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# ユーザー定義階層の追加または削除
  ディメンションでのユーザー定義階層の追加と削除は、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のディメンション デザイナーにある **[ディメンション構造]** タブで実行します。  
  
 ユーザー定義階層を追加した場合、この階層は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでインスタンス化され、ディメンションが処理されるまで、ユーザーが使用することはできません。 詳細については、「[多次元モデル データベース &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md)」および「[多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)」を参照してください。  
  
### ディメンションにユーザー定義階層を追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、適切な [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを開き、作業するディメンションを開きます。  
  
     ディメンションは、ディメンション デザイナーの **[ディメンション構造]** タブに表示されます。  
  
2.  ユーザー定義階層で使用する属性を、**[属性]** ペインから **[階層]** ペインにドラッグします。  
  
3.  追加の属性をドラッグして、ユーザー定義階層内にレベルを形成します。  
  
     階層内で属性が表示される順序は重要です。 たとえば、時間階層では、階層の一覧で日よりも年が上に表示される必要があります。  
  
4.  必要に応じて、レベルを適切な位置にドラッグして、ユーザー定義階層内でレベルを再配置します。  
  
5.  必要に応じて、ユーザー定義階層またはそのレベルのプロパティを変更します。  
  
     たとえば、ユーザー定義階層の名前を指定したり、その階層の 1 つ以上のレベルの名前を変更したり、All レベルのカスタム名を定義したりできます。 詳細については、「[ユーザー階層プロパティ](../Topic/User%20Hierarchy%20Properties.md)」および「[レベルのプロパティ - ユーザー階層](../Topic/Level%20Properties%20-%20user%20hierarchies.md)」を参照してください。  
  
    > [!NOTE]  
    >  既定では、ユーザー定義階層は単なるパスです。これにより、ユーザーは情報をドリル ダウンできます。 ただし、レベル間にリレーションシップが存在する場合は、レベル間の属性リレーションシップを構成することにより、クエリ パフォーマンスを向上できます。 詳細については、「[属性リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」および「[属性リレーションシップの定義](../../analysis-services/multidimensional-models/define-attribute-relationships.md)」を参照してください。  
  
### ディメンションからユーザー定義階層を削除するには  
  
-   **[ディメンション構造]** タブの **[階層]** ペインで、削除するユーザー定義階層をクリックします。 ツール バーの **[削除]** をクリックします。  
  
     - または -  
  
-   **[階層]** ペインで、削除するユーザー定義階層を右クリックし、**[削除]** をクリックします。  
  
     - または -  
  
-   ユーザー定義階層をデザイン画面外にドラッグします。  
  
## 参照  
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [ユーザー定義階層の作成](../../analysis-services/multidimensional-models/create-user-defined-hierarchies.md)  
  
  