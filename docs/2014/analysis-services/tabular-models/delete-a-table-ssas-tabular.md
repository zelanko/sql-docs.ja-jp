---
title: テーブル (SSAS テーブル) の削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 142a775415da489e67bc00b048651209a2a30179
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224762"
---
# <a name="delete-a-table-ssas-tabular"></a>テーブルの削除 (SSAS テーブル)
  モデル デザイナーでは、モデル ワークスペース データベース内の不要なテーブルを削除できます。 テーブルを削除しても、元のソース データには影響しません。インポートして作業していたデータにのみ影響します。 テーブルの削除を元に戻すことはできません。  
  
### <a name="to-delete-a-table"></a>テーブルを削除するには  
  
-   削除するテーブルのモデル デザイナーの下にあるタブを右クリックし、 **[削除]** をクリックします。  
  
## <a name="considerations-when-deleting-tables"></a>テーブルを削除する際の注意事項  
  
-   テーブルを削除すると、テーブルを含んでいるタブ全体が削除されます。  
  
-   そのテーブルにメジャーが関連付けられている場合、メジャーの定義も削除されます。  
  
-   そのテーブルを使用して計算列を作成していた場合、そのテーブルの列も削除されます。削除対象のテーブル列を他のテーブルの計算列で使用している場合は、エラーが表示されます。  
  
## <a name="see-also"></a>参照  
 [テーブルと列&#40;SSAS 表形式&#41;](tables-and-columns-ssas-tabular.md)  
  
  
