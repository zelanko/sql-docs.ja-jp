---
title: "インポート状態 (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 306577c5-e7d7-4cff-aff4-efb5c6354036
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e1427dc1d936f950b57755d6992d0b80553a3046
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="import-statuses-master-data-services"></a>インポート状態 (マスター データ サービス)
  **[ステージング バッチ]** ページの **[統合管理]** 機能領域に表示される状態は次のとおりです。  
  
|状態|Description|Status_ID|  
|------------|-----------------|----------------|  
|実行用のキューに登録済み|バッチ処理が開始されていません。|@shouldalert|  
|実行中|バッチ処理中です。|2|  
|[完了]|バッチ処理が完了しています。|3|  
|消去用のキューに登録済み|バッチ処理が完了しており、消去されます。|4|  
|クリア|バッチ処理が消去されました。|5|  
  
## <a name="see-also"></a>参照  
 [概要: テーブルからデータをインポートする (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)  
  
  
