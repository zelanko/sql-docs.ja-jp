---
title: "列の削除 (SSAS 表形式) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 32550571898b6c99d76ad256b123285951edfae4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="delete-a-column-ssas-tabular"></a>列の削除 (SSAS テーブル)
  このトピックでは、テーブル モデルのテーブルから列を削除する方法について説明します。  
  
## <a name="delete-a-model-table-column"></a>モデル テーブルの列の削除  
  
> [!NOTE]  
>  モデル テーブルから列を削除しても、列はパーティションのクエリ定義からは削除されません。 削除する列がパーティションの一部である場合、パーティションのクエリ定義から手動で列を削除する必要があります。 パーティションのクエリ定義から列を削除しない場合、列にクエリが実行されてデータが返されますが、モデル テーブルには処理操作時に値が設定されません。 詳細については、「 [パーティション (SSAS テーブル)](../../analysis-services/tabular-models/partitions-ssas-tabular.md)」を参照してください。  
  
#### <a name="to-delete-a-model-table-column"></a>モデル テーブルの列を削除するには  
  
-   モデル デザイナーの削除対象の列が含まれるテーブルで列を右クリックし、 **[削除]**をクリックします。  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>[テーブルのプロパティ] ダイアログ ボックスを使用してモデル テーブルの列を削除するには  
  
1.  モデル デザイナーで削除対象の列が含まれるテーブルをクリックし、 **[テーブル]** メニュー、  **[テーブルのプロパティ]**の順にクリックします。  
  
2.  **[列名の取得元]**で、 **[モデル]** を選択します (*ソースと異なる場合、モデル テーブルの列名を使用します*)。  
  
3.  **[テーブルのプロパティの編集]** ダイアログ ボックスのテーブル プレビュー ウィンドウで、削除する列をオフにしてから、 **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [列のテーブルへの追加 (SSAS テーブル)](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [パーティション (SSAS テーブル)](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
