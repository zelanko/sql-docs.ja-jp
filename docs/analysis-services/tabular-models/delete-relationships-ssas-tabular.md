---
title: "リレーションシップの削除 (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
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
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 54f2d9205ec7e8815572e9107e6319262c343edd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="delete-relationships-ssas-tabular"></a>リレーションシップの削除 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]ダイアグラム ビューでモデル デザイナーを使用して、または [リレーションシップの管理] ダイアログ ボックスを使用して既存のリレーションシップを削除することができます。 テーブル モデルでリレーションシップがどのように使用されるかについては、「 [リレーションシップ (SSAS テーブル)](../../analysis-services/tabular-models/relationships-ssas-tabular.md)」を参照してください。  
  
## <a name="considerations-for-deleting-relationships"></a>リレーションシップの削除に関する注意事項  
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
 [リレーションシップ &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/relationships-ssas-tabular.md)   
 [2 つのテーブル間のリレーションシップの作成 (SSAS テーブル)](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
