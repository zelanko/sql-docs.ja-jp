---
title: "バックアップと APS PDW のハードウェアの概要の読み込み"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "エンド ツー エンドのデータ ウェアハウス ソリューション Analytics Platform System (APS) 上で SQL Server 並列データ ウェアハウス (PDW) を展開するには、データ ウェアハウスをバックアップして、データの読み込みの計画を作成する必要があります。"
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 3a2ae046-f8d8-4a5c-b3c1-6ecee005df6c
caps.latest.revision: "9"
ms.openlocfilehash: 0bdf529aacf1644f55cd44da3d0a7590e509a323
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="backup-and-loading-hardware-overview"></a>バックアップとハードウェアの概要の読み込み
エンド ツー エンドのデータ ウェアハウス ソリューション Analytics Platform System (APS) 上で SQL Server 並列データ ウェアハウス (PDW) を展開するには、データ ウェアハウスをバックアップして、データの読み込みの計画を作成する必要があります。 取得して、ビジネス要件を満たすサーバーをバックアップおよび読み込みを構成するには、このガイドを使用します。  
  
## <a name="acquire-and-configure-backup-servers"></a>取得して、バックアップ サーバーを構成します。  
![バックアップ プロセス](media/backup-process.png "バックアップ プロセス")  
  
PDW のデータベースをバックアップするため、1 つまたは複数のバックアップ サーバーを作成する必要があります。 既存のハードウェアを使用したり、新しいハードウェアを購入することができます。 詳細については、次を参照してください。[取得およびサーバーのバックアップを構成](acquire-and-configure-backup-server.md)です。 この手順では、[サーバー容量の計画ワークシートをバックアップ](backup-capacity-planning-worksheet.md)バックアップに適したソリューションを計画するときにします。  
  
## <a name="acquire-and-configure-loading-servers"></a>取得し、読み込みのサーバーを構成します。  
![読み込みプロセス](media/loading-process.png "読み込みプロセス")  
  
データを読み込むには、1 つまたは複数のサーバーの読み込みが必要です。 新しいサーバーを購入することや、独自の既存の ETL または他のサーバーを使用できます。 詳細については、次を参照してください。 [Acquire 読み込み中にサーバーを構成および](acquire-and-configure-loading-server.md)です。 この手順では、[サーバー容量の計画ワークシートを読み込む](loading-server-capacity-planning-worksheet.md)を読み込み中に適したソリューションを計画します。  
  
## <a name="see-also"></a>参照  
[バックアップと復元の概要](backup-and-restore-overview.md)  
[ロードの概要](load-overview.md)  
  
