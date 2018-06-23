---
title: ディメンションの順序の定義 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d9a0fa0464c2263d21e50fa53c3b577a42d0a950
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174568"
---
# <a name="define-the-ordering-for-a-dimension"></a>ディメンションの順序の定義
  キューブまたはディメンションに属性の順序指定の拡張機能を追加して、属性のメンバーの順序付け方法を指定します。 メンバーは、属性の名前またはキー、あるいは、属性リレーションシップに基づいた別の属性の名前またはキーによって順序を指定できます。 既定では、名前によってメンバーの順序を指定します。 この拡張機能の変更、`OrderBy`と`OrderByAttributeID`ディメンションの属性のプロパティ設定します。  
  
 属性の順序を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[属性の順序の指定]** オプションを選択します。 このウィザードでは、属性の順序の適用先となるディメンションを選択し、選択したディメンションの属性の順序付け方法を指定する手順が示されます。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[属性の順序の指定]** ページで、属性の順序の適用先になるディメンションを指定します。 選択したこのディメンションに追加された属性の順序指定の拡張機能により、ディメンションが変更されます。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
## <a name="specifying-ordering"></a>順序の指定  
 **[属性の順序の指定]** の 2 ページ目で、ディメンションのすべての属性を順序付ける方法を指定します。  
  
 **[属性の並べ替え]** 列で、順序付けに使用する属性を変更できます。 メンバーの順序付けに使用する属性が一覧にない場合は、一覧を下にスクロールし、 **\<新しい属性 ...> >** を開くには、**列を選択して**することができます ダイアログ ボックスディメンション テーブルで列を選択します。 **[列の選択]** ダイアログ ボックスを使用して列を選択すると、属性のメンバーを順序付ける追加の属性が作成されます。  
  
 **[条件]** 列で、 **[キー]** または **[名前]** のどちらによって属性のメンバーを順序付けるかを選択できます。  
  
  