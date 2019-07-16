---
title: メンバー グループの定義 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1da226353847409f1d808472dc155cb2055395cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179600"
---
# <a name="attribute-properties---define-member-groups"></a>属性のプロパティ - メンバー グループを定義する
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  特定の属性に多数のメンバーが存在する場合は、そのメンバーをバケットにグループ化すると、階層内のデータを参照するときに表示されるメンバーの数を減らすことができます。 メンバーをグループ化するバケットの数を指定したり、バケットの名前付けスキーマを設定したりできます。 詳細については、[「属性メンバーのグループ化 (分離)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
 メンバーをグループ化するには、**DiscretizationMethod** プロパティを設定します。このプロパティには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の **[プロパティ]** ウィンドウからアクセスできます。  
  
 メンバー グループを作成した場合、ディメンションを処理するまで他のユーザーは変更内容を利用できません。 詳細については、「[多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)」を参照してください。  
  
### <a name="to-create-member-groups"></a>メンバー グループを作成するには  
  
1.  作業するディメンションを開きます。 既定では、 **[ディメンション構造]** タブが表示されます。  
  
2.  **[属性]** で、グループ化するメンバーの属性を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[DiscretizationMethod]** の横のドロップダウン リストから、メンバーのグループ化方法を選択します。 **[DiscretizationMethod]** の設定の詳細については、「[属性メンバーのグループ化 (分離)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
  
