---
title: ディメンションの順序の定義 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f2e9dfce4abc66e9fa77a7d429c3cdd9a306c69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209143"
---
# <a name="bi-wizard---define-the-ordering-for-a-dimension"></a>BI ウィザード - ディメンションの順序の定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブまたはディメンションに属性の順序指定の拡張機能を追加して、属性のメンバーの順序付け方法を指定します。 メンバーは、属性の名前またはキー、あるいは、属性リレーションシップに基づいた別の属性の名前またはキーによって順序を指定できます。 既定では、名前によってメンバーの順序を指定します。 この拡張機能により、ディメンション内にある属性の **OrderBy** および **OrderByAttributeID** プロパティ設定が変更されます。  
  
 属性の順序を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[属性の順序の指定]** オプションを選択します。 このウィザードでは、属性の順序の適用先となるディメンションを選択し、選択したディメンションの属性の順序付け方法を指定する手順が示されます。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[属性の順序の指定]** ページで、属性の順序の適用先になるディメンションを指定します。 選択したこのディメンションに追加された属性の順序指定の拡張機能により、ディメンションが変更されます。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
## <a name="specifying-ordering"></a>順序の指定  
 **[属性の順序の指定]** の 2 ページ目で、ディメンションのすべての属性を順序付ける方法を指定します。  
  
 **[属性の並べ替え]** 列で、順序付けに使用する属性を変更できます。 一覧でメンバーの順序付けに使用する属性がない場合、一覧を下までスクロールを選び **\<新しい属性 ...> >** を開く、**列を選択して** ダイアログ ボックスで行うことができますディメンション テーブルに列を選択します。 **[列の選択]** ダイアログ ボックスを使用して列を選択すると、属性のメンバーを順序付ける追加の属性が作成されます。  
  
 **[条件]** 列で、 **[キー]** または **[名前]** のどちらによって属性のメンバーを順序付けるかを選択できます。  
  
  
