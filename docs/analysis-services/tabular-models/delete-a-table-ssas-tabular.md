---
title: "テーブルの削除 (SSAS 表形式) |Microsoft ドキュメント"
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
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1d3437449a05b5e1f60083135e020171b3d1e916
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="delete-a-table-ssas-tabular"></a>テーブルの削除 (SSAS テーブル)
  モデル デザイナーでは、モデル ワークスペース データベース内の不要なテーブルを削除できます。 テーブルを削除しても、元のソース データには影響しません。インポートして作業していたデータにのみ影響します。 テーブルの削除を元に戻すことはできません。  
  
### <a name="to-delete-a-table"></a>テーブルを削除するには  
  
-   削除するテーブルのモデル デザイナーの下にあるタブを右クリックし、 **[削除]**をクリックします。  
  
## <a name="considerations-when-deleting-tables"></a>テーブルを削除する際の注意事項  
  
-   テーブルを削除すると、テーブルを含んでいるタブ全体が削除されます。  
  
-   そのテーブルにメジャーが関連付けられている場合、メジャーの定義も削除されます。  
  
-   そのテーブルを使用して計算列を作成していた場合、そのテーブルの列も削除されます。削除対象のテーブル列を他のテーブルの計算列で使用している場合は、エラーが表示されます。  
  
## <a name="see-also"></a>参照  
 [テーブルと列 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  

