---
title: テーブルの削除 |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9a9269457d973da6b56f9e7990c31700dafcad9
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="delete-a-table"></a>テーブルを削除します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  モデル デザイナーでは、モデル ワークスペース データベース内の不要なテーブルを削除できます。 テーブルを削除しても、元のソース データには影響しません。インポートして作業していたデータにのみ影響します。 テーブルの削除を元に戻すことはできません。  
  
### <a name="to-delete-a-table"></a>テーブルを削除するには  
  
-   削除するテーブルのモデル デザイナーの下にあるタブを右クリックし、 **[削除]** をクリックします。  
  
## <a name="considerations-when-deleting-tables"></a>テーブルを削除する際の注意事項  
  
-   テーブルを削除すると、テーブルを含んでいるタブ全体が削除されます。  
  
-   そのテーブルにメジャーが関連付けられている場合、メジャーの定義も削除されます。  
  
-   そのテーブルを使用して計算列を作成していた場合、そのテーブルの列も削除されます。削除対象のテーブル列を他のテーブルの計算列で使用している場合は、エラーが表示されます。  
  
## <a name="see-also"></a>参照  
 [テーブルと列](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
