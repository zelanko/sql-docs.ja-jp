---
title: 既定のトレース ログ ファイルの無効化 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a816912147038cd49b35ba29bfec732410c2ca91
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616050"
---
# <a name="default-trace-log-files-disabled"></a>既定のトレース ログ ファイルの無効化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、sp_configure システム ストアド プロシージャの default trace enabled オプションの値を調べて、既定のトレースが ON (1) または OFF (0) のどちらに設定されているかを確認します。 このオプションを有効にした場合、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に対する構成および DDL の変更に関する情報が既定のトレースによって提供されます。 この情報は、顧客および [!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービスが、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]に関する問題のトラブルシューティングを行うときに役立つ場合があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 sp_configure stored ストアド プロシージャを使用して default trace enabled の値を 1 に設定することで、トレースを有効にしてください。  
  
## <a name="for-more-information"></a>詳細情報  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
