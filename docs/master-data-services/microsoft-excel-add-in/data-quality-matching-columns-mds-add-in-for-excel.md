---
title: "(MDS アドインを Excel の) 列を照合するデータ品質 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4ce8ddcdbf8c29663640025ad40b4e01e44d99c1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>データ品質照合の列 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]でデータを照合した後、**データ品質**グループ リボンをクリックできます**詳細の表示**照合の詳細を提供する列を表示します。  
  
 次の表に、データの照合時に表示される列を示します。  
  
|名前|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|類似レコードのグループ化に使用する一意識別子です。 類似するすべての行は、同じ **CLUSTER_ID**を持ちます。 **CLUSTER_ID** が行に対して表示されない場合、類似レコードが見つかっていません。|  
|**RECORD_ID**|レコードの識別に使用する一意識別子です。 MDS リポジトリに格納されているコード値と同様に、レコードの識別に使用される値です。 照合が実行されるたびに自動的に生成されます。|  
|**PIVOT_MARK**|他のレコードと比較される任意のレコードで、スコアの値はありません。|  
|**SCORE**|グループ内のレコードがピボット レコードとどの程度類似しているかを表します。 このスコアは DQS によって決定されます。 スコアが表示されない場合、そのレコードは他のレコードのピボットであるか、照合が見つかりませんでした。|  
  
## <a name="see-also"></a>参照  
 [Excel 用の MDS アドインでは、照合データ品質](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [類似のデータ &#40; と一致します。MDS 用のアドインの Excel &#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [データ照合](../../data-quality-services/data-matching.md)  
  
  
