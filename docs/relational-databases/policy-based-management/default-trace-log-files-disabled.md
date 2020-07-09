---
title: 既定のトレース ログ ファイルの無効化 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 2e8335f3fa61cc446db748a4913d6eaa22388659
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749462"
---
# <a name="default-trace-log-files-disabled"></a>既定のトレース ログ ファイルの無効化
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このルールでは、sp_configure システム ストアド プロシージャの default trace enabled オプションの値を調べて、既定のトレースが ON (1) または OFF (0) のどちらに設定されているかを確認します。 このオプションを有効にした場合、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に対する構成および DDL の変更に関する情報が既定のトレースによって提供されます。 この情報は、顧客および [!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービスが、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]に関する問題のトラブルシューティングを行うときに役立つ場合があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 sp_configure stored ストアド プロシージャを使用して default trace enabled の値を 1 に設定することで、トレースを有効にしてください。  
  
## <a name="for-more-information"></a>詳細情報  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
