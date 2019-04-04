---
title: Analysis Services 表形式モデルの計算 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 53455f542e10e816aa55272026a875cf3cf87107
ms.sourcegitcommit: 38076f423663bdbb42f325e3d0624264e05beda1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2018
ms.locfileid: "52984073"
---
# <a name="calculations-in-tabular-models"></a>表形式モデルの計算
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  データをモデルにインポートした後、計算を追加して、データの拡張、結合、要約、およびセキュリティの確保を実行することができます。 テーブル モデルでは、カスタムの計算を作成するための Data Analysis Expressions (DAX) という数式言語を使用します。 テーブル モデルでは、 *計算列*、 *メジャー*、および *行フィルター*に使用される計算を DAX の数式を使用して作成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[テーブル モデルでの DAX について](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|テーブル モデルの計算列、メジャー、および行フィルターに対して計算を作成する際に使用される Data Analysis Expressions (DAX) の数式言語について説明します。|  
|[DirectQuery モードでの DAX 数式の互換性](http://msdn.microsoft.com/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|相違点について説明し、DirectQuery モードではサポートされない関数、およびサポートはされるが異なる結果を返す可能性のある一連の関数を示します。|  
|[Data Analysis Expressions (DAX) リファレンス](http://msdn.microsoft.com/70a82136-0926-4a91-bcb3-e18e82593b0d)|このセクションでは、DAX の構文、演算子、および関数について詳しく説明します。|  
  
> [!NOTE]  
>  計算の作成に伴うタスクの実行手順は、このセクションには記載されていません。 計算は、計算列、メジャー、および行フィルター (ロール単位) で指定されるため、DAX の数式の作成先についての説明も、これらの各機能に関連したタスクで説明します。 詳細については、[計算列を作成する](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md)、[の作成と管理のメジャー](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)、および[作成と管理の役割](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)を参照してください。  
  
> [!NOTE]  
>  テーブル モデルをクエリする際にも DAX は使用できますが、このセクションの各トピックでは、DAX の数式を使用した計算の作成に的を絞って説明します。  
  
  
