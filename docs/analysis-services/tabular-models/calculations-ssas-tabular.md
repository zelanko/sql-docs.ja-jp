---
title: "計算 (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9f2d85a5064b41a5cae0fd63cda735ea6edcd3a2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="calculations-ssas-tabular"></a>計算 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]モデルにデータをインポートした後は、集計、フィルター処理、拡張、結合、およびデータを保護する計算式を追加できます。 テーブル モデルでは、カスタムの計算を作成するための Data Analysis Expressions (DAX) という数式言語を使用します。 テーブル モデルでは、 *計算列*、 *メジャー*、および *行フィルター*に使用される計算を DAX の数式を使用して作成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[テーブル モデルでの DAX について (SSAS テーブル)](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|テーブル モデルの計算列、メジャー、および行フィルターに対して計算を作成する際に使用される Data Analysis Expressions (DAX) の数式言語について説明します。|  
|[DirectQuery モードでの DAX 数式の互換性 (SQL Server Analysis Services)](http://msdn.microsoft.com/en-us/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|相違点について説明し、DirectQuery モードではサポートされない関数、およびサポートはされるが異なる結果を返す可能性のある一連の関数を示します。|  
|[Data Analysis Expressions (DAX) リファレンス](http://msdn.microsoft.com/en-us/70a82136-0926-4a91-bcb3-e18e82593b0d)|このセクションでは、DAX の構文、演算子、および関数について詳しく説明します。|  
  
> [!NOTE]  
>  計算の作成に伴うタスクの実行手順は、このセクションには記載されていません。 計算は、計算列、メジャー、および行フィルター (ロール単位) で指定されるため、DAX の数式の作成先についての説明も、これらの各機能に関連したタスクで説明します。 詳細については、「[計算列の作成 (SSAS テーブル)](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md)」、「[メジャーを作成および管理する (SSAS テーブル)](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)」、および「[ロールの作成および管理 (SSAS テーブル)](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)」を参照してください。  
  
> [!NOTE]  
>  テーブル モデルをクエリする際にも DAX は使用できますが、このセクションの各トピックでは、DAX の数式を使用した計算の作成に的を絞って説明します。  
  
  
