---
title: 計算 (SSAS テーブル) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f17c8ab9ebf08379bf0b989924221995d7eaf891
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174012"
---
# <a name="calculations-ssas-tabular"></a>計算 (SSAS テーブル)
  データをモデルにインポートした後、計算を追加して、データの拡張、結合、要約、およびセキュリティの確保を実行することができます。 テーブル モデルでは、カスタムの計算を作成するための Data Analysis Expressions (DAX) という数式言語を使用します。 テーブル モデルでは、 *計算列*、 *メジャー*、および *行フィルター*に使用される計算を DAX の数式を使用して作成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[テーブル モデルにおける DAX を理解する&#40;SSAS 表形式&#41;](understanding-dax-in-tabular-models-ssas-tabular.md)|テーブル モデルの計算列、メジャー、および行フィルターに対して計算を作成する際に使用される Data Analysis Expressions (DAX) の数式言語について説明します。|  
|[DirectQuery モードでの数式の互換性](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|相違点について説明し、DirectQuery モードではサポートされない関数、およびサポートはされるが異なる結果を返す可能性のある一連の関数を示します。|  
|[Data Analysis Expressions &#40;DAX&#41;参照](https://msdn.microsoft.com/library/gg413422(v=sql.120).aspx)|このセクションでは、DAX の構文、演算子、および関数について詳しく説明します。|  
  
> [!NOTE]  
>  計算の作成に伴うタスクの実行手順は、このセクションには記載されていません。 計算は、計算列、メジャー、および行フィルター (ロール単位) で指定されるため、DAX の数式の作成先についての説明も、これらの各機能に関連したタスクで説明します。 詳細については、「[計算列の作成 (SSAS テーブル)](ssas-calculated-columns-create-a-calculated-column.md)」、「[メジャーを作成および管理する (SSAS テーブル)](measures-ssas-tabular.md)」、および「[ロールの作成および管理 (SSAS テーブル)](roles-ssas-tabular.md)」を参照してください。  
  
> [!NOTE]  
>  テーブル モデルをクエリする際にも DAX は使用できますが、このセクションの各トピックでは、DAX の数式を使用した計算の作成に的を絞って説明します。  
  
  