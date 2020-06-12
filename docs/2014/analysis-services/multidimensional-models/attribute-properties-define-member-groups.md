---
title: メンバーグループを定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95f9516c7a0077e97af348afa863fe15c8d4528b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544754"
---
# <a name="define-member-groups"></a>メンバー グループを定義する
  特定の属性に多数のメンバーが存在する場合は、そのメンバーをバケットにグループ化すると、階層内のデータを参照するときに表示されるメンバーの数を減らすことができます。 メンバーをグループ化するバケットの数を指定したり、バケットの名前付けスキーマを設定したりできます。 詳細については、[「属性メンバーのグループ化 (分離)](attribute-properties-group-attribute-members.md)」を参照してください。  
  
 メンバーをグループ化するには、 **DiscretizationMethod** プロパティを設定します。このプロパティには、 **の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ウィンドウからアクセスできます。  
  
 メンバー グループを作成した場合、ディメンションを処理するまで他のユーザーは変更内容を利用できません。 詳細については、「[多次元モデルオブジェクトの処理](processing-a-multidimensional-model-analysis-services.md)」を参照してください。  
  
### <a name="to-create-member-groups"></a>メンバー グループを作成するには  
  
1.  作業するディメンションを開きます。 既定では、 **[ディメンション構造]** タブが表示されます。  
  
2.  **[属性]** で、グループ化するメンバーの属性を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[DiscretizationMethod]** の横のドロップダウン リストから、メンバーのグループ化方法を選択します。 **[DiscretizationMethod]** の設定の詳細については、「[属性メンバーのグループ化 (分離)](attribute-properties-group-attribute-members.md)」を参照してください。  
  
  
