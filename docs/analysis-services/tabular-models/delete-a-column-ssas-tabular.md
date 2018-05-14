---
title: 列の削除 |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e850740754fea16aa82c60b3abda9f86bafeaff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="delete-a-column"></a>列の削除 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  この記事では、テーブル モデル テーブルから列を削除する方法について説明します。  
  
## <a name="delete-a-model-table-column"></a>モデル テーブルの列の削除  
  
> [!NOTE]  
>  モデル テーブルから列を削除しても、列はパーティションのクエリ定義からは削除されません。 削除する列がパーティションの一部である場合、パーティションのクエリ定義から手動で列を削除する必要があります。 パーティションのクエリ定義から列を削除しない場合、列にクエリが実行されてデータが返されますが、モデル テーブルには処理操作時に値が設定されません。 詳細については、次を参照してください。[パーティション](../../analysis-services/tabular-models/partitions-ssas-tabular.md)です。  
  
#### <a name="to-delete-a-model-table-column"></a>モデル テーブルの列を削除するには  
  
-   モデル デザイナーの削除対象の列が含まれるテーブルで列を右クリックし、 **[削除]** をクリックします。  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>[テーブルのプロパティ] ダイアログ ボックスを使用してモデル テーブルの列を削除するには  
  
1.  モデル デザイナーで削除対象の列が含まれるテーブルをクリックし、 **[テーブル]** メニュー、  **[テーブルのプロパティ]** の順にクリックします。  
  
2.  **[列名の取得元]** で、 **[モデル]** を選択します (*ソースと異なる場合、モデル テーブルの列名を使用します*)。  
  
3.  **[テーブルのプロパティの編集]** ダイアログ ボックスのテーブル プレビュー ウィンドウで、削除する列をオフにしてから、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [テーブルに列を追加します。](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [パーティション](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
