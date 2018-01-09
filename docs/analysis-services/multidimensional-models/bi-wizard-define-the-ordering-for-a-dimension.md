---
title: "ディメンションの順序の定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
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
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 128efeccdeb3b99a580bd4e2f2ba360df874c222
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="bi-wizard---define-the-ordering-for-a-dimension"></a>BI ウィザード - は、ディメンションの順序を定義します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]属性の拡張機能で、キューブまたはディメンションに属性のメンバーの順序付け方法を指定の順序を追加します。 メンバーは、属性の名前またはキー、あるいは、属性リレーションシップに基づいた別の属性の名前またはキーによって順序を指定できます。 既定では、名前によってメンバーの順序を指定します。 この拡張機能により、ディメンション内にある属性の **OrderBy** および **OrderByAttributeID** プロパティ設定が変更されます。  
  
 属性の順序を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[属性の順序の指定]** オプションを選択します。 このウィザードでは、属性の順序の適用先となるディメンションを選択し、選択したディメンションの属性の順序付け方法を指定する手順が示されます。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[属性の順序の指定]** ページで、属性の順序の適用先になるディメンションを指定します。 選択したこのディメンションに追加された属性の順序指定の拡張機能により、ディメンションが変更されます。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
## <a name="specifying-ordering"></a>順序の指定  
 **[属性の順序の指定]** の 2 ページ目で、ディメンションのすべての属性を順序付ける方法を指定します。  
  
 **[属性の並べ替え]** 列で、順序付けに使用する属性を変更できます。 メンバーの順序付けに使用する属性が一覧にない場合は、一覧を下にスクロールし、 **\<新しい属性 ...> >**を開くには、**列を選択して**することができます ダイアログ ボックスディメンション テーブルで列を選択します。 **[列の選択]** ダイアログ ボックスを使用して列を選択すると、属性のメンバーを順序付ける追加の属性が作成されます。  
  
 **[条件]** 列で、 **[キー]** または **[名前]**のどちらによって属性のメンバーを順序付けるかを選択できます。  
  
  
