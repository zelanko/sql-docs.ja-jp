---
title: "ディメンションの書き戻しを有効にする |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 69390faf39311c3b7072e06aff2b64fcafd9a62c
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="bi-wizard---enable-dimension-writeback"></a>BI ウィザード - ディメンションの書き戻しを有効にします。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
キューブまたはディメンションにディメンション書き戻し拡張機能を追加すると、ユーザーはディメンション構造とメンバーを手動で変更できます。 書き込みが可能なディメンションに加えた更新は、ディメンション テーブルに直接記録されます。 この拡張機能により、ディメンションの **WriteEnabled** プロパティ設定が変更されます。  
  
 ディメンションの書き戻しを追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[ディメンションの書き戻しの有効化]** オプションを選択します。 次に、ウィザードに従って、ディメンションの書き戻しを適用するディメンションを選択し、そのディメンションにこのオプションを設定します。  
  
> [!NOTE]  
>  書き戻しは、SQL Server リレーショナル データベースおよびデータ マートでのみサポートされます。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[ディメンションの書き戻しの有効化]** ページで、ディメンションの書き戻しを適用するディメンションを指定します。 選択したこのディメンションに追加されたディメンション書き戻し拡張機能により、ディメンションが変更されます。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
## <a name="setting-dimension-writeback-capability"></a>ディメンションの書き戻し機能の設定  
 ウィザードの **[ディメンションの書き戻しの有効化]** の 2 ページ目で、実際に **[ディメンションへの書き戻しを有効にする]** オプションを設定します。 このオプションを選択すると、ディメンションの **WriteEnabled** プロパティが自動的に **True**に設定されます。 このオプションの選択を解除すると、このプロパティは自動的に **False**に設定されます。  
  
## <a name="remarks"></a>解説  
 新しいメンバーを作成するときは、ディメンションにすべての属性を含める必要があります。 ディメンションのキー属性値を指定せずにメンバーを挿入することはできません。 このため、メンバーの作成は、ディメンション テーブルに定義されている制約 (NULL 以外のキー値など) に拘束されます。 必要に応じて、ディメンション プロパティで指定された列 ( **CustomRollupColumn**、 **CustomRollupPropertiesColumn** 、または **UnaryOperatorColumn** ディメンション プロパティで指定した列など) についても考慮する必要があります。  
  
> [!WARNING]  
>  SQL Azure をデータ ソースとして使用して Analysis Services データベースへの書き戻しを実行すると、操作は失敗します。 これは仕様による結果です。既定では、複数のアクティブな結果セット (MARS) を有効にするプロバイダー オプションがオンになっていないためです。  
>   
>  これを回避するには、次の設定を接続文字列に追加し、MARS をサポートして書き戻しを有効にします。  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  詳細については、「[複数のアクティブな結果セット &#40;MARS&#41; の使用](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [書き込み許可ディメンション](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
