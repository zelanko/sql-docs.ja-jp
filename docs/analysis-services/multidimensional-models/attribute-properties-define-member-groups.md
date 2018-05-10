---
title: メンバー グループを定義する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 15e02bff085d6a53d3573cbb354948b101a67513
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="attribute-properties---define-member-groups"></a>属性のプロパティ - メンバー グループの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  特定の属性に多数のメンバーが存在する場合は、そのメンバーをバケットにグループ化すると、階層内のデータを参照するときに表示されるメンバーの数を減らすことができます。 メンバーをグループ化するバケットの数を指定したり、バケットの名前付けスキーマを設定したりできます。 詳細については、[「属性メンバーのグループ化 (分離)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
 メンバーをグループ化するには、**DiscretizationMethod** プロパティを設定します。このプロパティには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の **[プロパティ]** ウィンドウからアクセスできます。  
  
 メンバー グループを作成した場合、ディメンションを処理するまで他のユーザーは変更内容を利用できません。 詳細については、「[多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)」を参照してください。  
  
### <a name="to-create-member-groups"></a>メンバー グループを作成するには  
  
1.  作業するディメンションを開きます。 既定では、 **[ディメンション構造]** タブが表示されます。  
  
2.  **[属性]** で、グループ化するメンバーの属性を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[DiscretizationMethod]** の横のドロップダウン リストから、メンバーのグループ化方法を選択します。 **[DiscretizationMethod]** の設定の詳細については、「[属性メンバーのグループ化 (分離)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
  
