---
title: "セッション スコープの作成の名前付きセット (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 87be5fc0a7e1c1afd663d70371342035ac0d1d1b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-named-sets---creating-session-scoped-named-sets"></a>名前付きセットの名前付きセット、セッション スコープの作成の MDX
  多次元式 (MDX) セッション全体で使用できる名前付きセットを作成するには、 [CREATE SET](../../../mdx/mdx-data-definition-create-set.md) ステートメントを使用します。 CREATE SET ステートメントを使用して作成された名前付きセットは、MDX セッションが閉じるまで削除されません。  
  
 このトピックで説明するように、WITH キーワードの構文は非常に単純で使いやすいものです。  
  
> [!NOTE]  
>  名前付きセットの詳細については、「[MDX での名前付きセットの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md)」をご覧ください。  
  
## <a name="create-set-syntax"></a>CREATE SET の構文  
 CREATE SET ステートメントの構文は、以下のとおりです。  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 CREATE SET の構文において、 `cube name` パラメーターには、名前付きセットのメンバーを格納するキューブの名前が入ります。 `cube name` パラメーターが指定されなかった場合は、名前付きセットのメンバーを格納するキューブとして、現在のキューブが使用されます。 さらに、 `Set_Identifier` パラメーターには名前付きセットの別名が入り、 `Set_Expression` パラメーターには名前付きセットの別名の参照先であるセット式が入ります。  
  
## <a name="create-set-example"></a>CREATE SET の例  
 次の例では、Store キューブに基づいて `SetCities_2_3` 名前付きセットを作成するために CREATE SET ステートメントを使用します。 `SetCities_2_3` 名前付きセットのメンバーは、City&#xA0;2 および City&#xA0;3 にあるストアです。  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 CREATE SET ステートメントを使って `SetCities_2_3` 名前付きセットを定義しているので、この名前付きセットは現在の MDX セッションが続く限り使用可能です。 次の例は、City&#xA0;2 と City&#xA0;3 のメンバーを返す有効なクエリです。 `SetCities_2_3` 名前付きセットを作成した後、セッションが閉じる前の任意の時点でこのクエリを実行できます。  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a>参照  
 [クエリ スコープの名前付きセットの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
