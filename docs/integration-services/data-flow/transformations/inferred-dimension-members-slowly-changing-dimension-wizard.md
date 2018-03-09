---
title: "推定ディメンション メンバー (緩やかに変化するディメンション ウィザード) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a6f638556c4e7f0f0fb14acbd05d843ebbceac4
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>[推定ディメンション メンバー] (緩やかに変化するディメンション ウィザード)
  **[推定ディメンション メンバー]** ダイアログ ボックスを使用すると、推定メンバーを使用するためのオプションを指定できます。 推定メンバーは、まだ読み込まれていないディメンション メンバーをファクト テーブルで参照するときに使用されます。 推定メンバーのデータが読み込まれると、新しいレコードを作成する代わりに、既存のレコードを更新できます。  
  
 このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[推定メンバー サポートを有効にする]**  
 推定メンバーを有効にすることを選択した場合は、次のどちらかのオプションを選択する必要があります。  
  
 **[変化する型を持つすべての列を NULL とする]**  
 新しい推定メンバー レコード内で、変化する型を持つすべての列に NULL 値を入力するかどうかを指定します。  
  
 **[現在のレコードが推定メンバーであるかどうかの識別にブール型の列を使用する]**  
 現在のレコードが推定メンバーであるかどうかを示すために、既存のブール型の列を使用するかどうかを指定します。  
  
 **[推定メンバー インジケーター]**  
 上記の、推定メンバーであるかどうかの識別にブール型の列を使用することを選択した場合は、一覧から列を選択します。  
  
## <a name="see-also"></a>参照  
 [緩やかに変化するディメンション ウィザードを使用して出力を構成する](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
