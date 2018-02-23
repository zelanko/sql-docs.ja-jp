---
title: "追加またはユーザー定義階層を削除する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a36cc61a153f559edc00c5b50cbd354abdfe7912
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="user-defined-hierarchies---add-or-delete-a-user-defined-hierarchy"></a>ユーザー定義階層の追加またはユーザー定義階層の削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
ディメンションでのユーザー定義階層の追加と削除は、 **のディメンション デザイナーにある** [ディメンション構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで実行します。  
  
 ユーザー定義階層を追加した場合、この階層は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでインスタンス化され、ディメンションが処理されるまで、ユーザーが使用することはできません。 詳細については、次を参照してください[多次元モデル データベース](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md)と[多次元モデル &#40; の処理。Analysis Services &#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a>ディメンションにユーザー定義階層を追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、適切な [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを開き、作業するディメンションを開きます。  
  
     ディメンションは、ディメンション デザイナーの **[ディメンション構造]** タブに表示されます。  
  
2.  ユーザー定義階層で使用する属性を、 **[属性]** ペインから **[階層]** ペインにドラッグします。  
  
3.  追加の属性をドラッグして、ユーザー定義階層内にレベルを形成します。  
  
     階層内で属性が表示される順序は重要です。 たとえば、時間階層では、階層の一覧で日よりも年が上に表示される必要があります。  
  
4.  必要に応じて、レベルを適切な位置にドラッグして、ユーザー定義階層内でレベルを再配置します。  
  
5.  必要に応じて、ユーザー定義階層またはそのレベルのプロパティを変更します。  
  
     たとえば、ユーザー定義階層の名前を指定したり、その階層の 1 つ以上のレベルの名前を変更したり、All レベルのカスタム名を定義したりできます。 詳細については、「 [ユーザー階層プロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)」および「 [レベルのプロパティ - ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)」を参照してください。  
  
    > [!NOTE]  
    >  既定では、ユーザー定義階層は単なるパスです。これにより、ユーザーは情報をドリル ダウンできます。 ただし、レベル間にリレーションシップが存在する場合は、レベル間の属性リレーションシップを構成することにより、クエリ パフォーマンスを向上できます。 詳細については、「 [属性リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) 」および「 [属性リレーションシップの定義](../../analysis-services/multidimensional-models/attribute-relationships-define.md)」を参照してください。  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a>ディメンションからユーザー定義階層を削除するには  
  
-   **[ディメンション構造]** タブの **[階層]** ペインで、削除するユーザー定義階層をクリックします。 ツール バーの **[削除]**をクリックします。  
  
     - または -  
  
-   **[階層]** ペインで、削除するユーザー定義階層を右クリックし、 **[削除]**をクリックします。  
  
     - または -  
  
-   ユーザー定義階層をデザイン画面外にドラッグします。  
  
## <a name="see-also"></a>参照  
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [ユーザー定義階層を作成します。](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
  
  
