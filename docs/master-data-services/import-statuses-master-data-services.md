---
title: インポート状態 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 306577c5-e7d7-4cff-aff4-efb5c6354036
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c3905312358c36688e4c20a5a78d6c5504c745aa
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35404124"
---
# <a name="import-statuses-master-data-services"></a>インポート状態 (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  **[ステージング バッチ]** ページの **[統合管理]** 機能領域に表示される状態は次のとおりです。  
  
|状態|[説明]|Status_ID|  
|------------|-----------------|----------------|  
|実行用のキューに登録済み|バッチ処理が開始されていません。|@shouldalert|  
|実行中|バッチ処理中です。|2|  
|[完了]|バッチ処理が完了しています。|3|  
|消去用のキューに登録済み|バッチ処理が完了しており、消去されます。|4|  
|クリア|バッチ処理が消去されました。|5|  
  
## <a name="see-also"></a>参照  
 [概要: テーブルからデータをインポートする (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)  
  
  
