---
title: "リレーションシップの削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: multidimensional-tabular
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 690224c1798494e75f6b26add07d51c3afa7134f
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="delete-relationships"></a>リレーションシップを削除します。 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
ダイアグラム ビューのモデル デザイナーまたは [リレーションシップの管理] ダイアログ ボックスを使用して、既存のリレーションシップを削除できます。 テーブル モデルでリレーションシップを使用する方法については、次を参照してください。[リレーションシップ](../../analysis-services/tabular-models/relationships-ssas-tabular.md)です。  
  
## <a name="considerations-for-deleting-relationships"></a>リレーションシップの削除に関する考慮事項  
 リレーションシップを削除するかどうかを判断する際には、以下の点に注意してください。  
  
-   リレーションシップの削除を元に戻す方法はありません。 リレーションシップを再作成することはできますが、これを行うには、モデル内の数式をすべて再計算する必要があります。 そのため、数式で使用されているリレーションシップを削除する場合は、このことを事前にチェックすることが重要です。  
  
-   2 つのテーブル間のリレーションシップを削除すると、それらのテーブルを参照する数式でエラーが発生します。  
  
-   Data Analysis Expression (DAX) の RELATED 関数は、テーブル間のリレーションシップを使用して関連する値をもう一方のテーブルで検索します。 リレーションシップが削除されると、この関数は異なる結果を返します。 詳細については、RELATED 関数 (DAX) を参照してください。  
  
-   リレーションシップを作成および削除すると、ピボットテーブルと数式の結果が変わるだけでなく、ブックの再計算も実行されます。この処理には、時間がかかることがあります。  
  
## <a name="delete-relationships"></a>リレーションシップの削除  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a>ダイアグラム ビューを使用してリレーションシップを削除するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]**をポイントして、 **[ダイアグラム ビュー]**をクリックします。  
  
2.  2 つのテーブルの間のリレーションシップの線を右クリックし、 **[削除]**をクリックします。  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a>[リレーションシップの管理] ダイアログ ボックスを使用してリレーションシップを削除するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[テーブル]** メニューをクリックし、 **[リレーションシップの管理]**をクリックします。  
  
2.  **[リレーションシップの管理]** ダイアログ ボックスで、一覧から 1 つまたは複数のリレーションシップを選択します。  
  
     複数のリレーションシップを選択するには、Ctrl キーを押しながら各リレーションシップをクリックします。  
  
3.  **[リレーションシップの削除]**をクリックします。  
  
4.  **[リレーションシップの管理]** ダイアログ ボックスで、 **[閉じる]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [リレーションシップ](../../analysis-services/tabular-models/relationships-ssas-tabular.md)   
 [リレーションシップを作成します。](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
