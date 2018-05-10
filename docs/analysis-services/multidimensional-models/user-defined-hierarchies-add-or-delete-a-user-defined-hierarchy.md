---
title: 追加またはユーザー定義階層を削除する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ce5421cf68b9eccb66f7ab701e6d149d73ec131f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="user-defined-hierarchies---add-or-delete-a-user-defined-hierarchy"></a>ユーザー定義階層の追加またはユーザー定義階層の削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ディメンションでのユーザー定義階層の追加と削除は、 **のディメンション デザイナーにある** [ディメンション構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで実行します。  
  
 ユーザー定義階層を追加した場合、この階層は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでインスタンス化され、ディメンションが処理されるまで、ユーザーが使用することはできません。 詳細については、次を参照してください。[多次元モデル データベース](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md)と[多次元モデルの処理&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)です。  
  
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
  
-   **[ディメンション構造]** タブの **[階層]** ペインで、削除するユーザー定義階層をクリックします。 ツール バーの **[削除]** をクリックします。  
  
     - または -  
  
-   **[階層]** ペインで、削除するユーザー定義階層を右クリックし、 **[削除]** をクリックします。  
  
     - または -  
  
-   ユーザー定義階層をデザイン画面外にドラッグします。  
  
## <a name="see-also"></a>参照  
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [ユーザー定義階層を作成します。](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
  
  
