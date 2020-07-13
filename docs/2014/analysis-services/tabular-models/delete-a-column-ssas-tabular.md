---
title: 列の削除 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
author: minewiskan
ms.author: owend
ms.openlocfilehash: c76256e03a7ad9a14f877ee1220a8dd6ced2ed8a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939743"
---
# <a name="delete-a-column-ssas-tabular"></a>列の削除 (SSAS テーブル)
  このトピックでは、テーブル モデルのテーブルから列を削除する方法について説明します。  
  
## <a name="delete-a-model-table-column"></a>モデル テーブルの列の削除  
  
> [!NOTE]  
>  モデル テーブルから列を削除しても、列はパーティションのクエリ定義からは削除されません。 削除する列がパーティションの一部である場合、パーティションのクエリ定義から手動で列を削除する必要があります。 パーティションのクエリ定義から列を削除しない場合、列にクエリが実行されてデータが返されますが、モデル テーブルには処理操作時に値が設定されません。 詳細については、「 [パーティション (SSAS テーブル)](partitions-ssas-tabular.md)」を参照してください。  
  
#### <a name="to-delete-a-model-table-column"></a>モデル テーブルの列を削除するには  
  
-   モデル デザイナーの削除対象の列が含まれるテーブルで列を右クリックし、 **[削除]** をクリックします。  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>[テーブルのプロパティ] ダイアログ ボックスを使用してモデル テーブルの列を削除するには  
  
1.  モデル デザイナーで削除対象の列が含まれるテーブルをクリックし、 **[テーブル]** メニュー、  **[テーブルのプロパティ]** の順にクリックします。  
  
2.  **[列名の取得元]** で、 **[モデル]** を選択します (*ソースと異なる場合、モデル テーブルの列名を使用します*)。  
  
3.  **[テーブルのプロパティの編集]** ダイアログ ボックスのテーブル プレビュー ウィンドウで、削除する列をオフにしてから、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;&#40;テーブルへの列の追加](add-columns-to-a-table-ssas-tabular.md)   
 [パーティション (SSAS テーブル)](partitions-ssas-tabular.md)  
  
  
