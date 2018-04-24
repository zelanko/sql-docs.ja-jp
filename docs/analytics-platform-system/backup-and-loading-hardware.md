---
title: バックアップとハードウェアの並列データ ウェアハウスの読み込み
description: ウェアハウス ソリューション Analytics Platform System (APS) で並列データ ウェアハウス (PDW) と、エンド ツー エンド データを展開するには、データ ウェアハウスをバックアップして、データの読み込みの計画を作成する必要があります。 取得して、ビジネス要件を満たすサーバーをバックアップおよび読み込みを構成するには、このガイドを使用します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4d7f7b6b4edea9dacab7287a7936b7fd87fd7973
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="backup-and-loading-hardware-overview---parallel-data-warehouse"></a>バックアップとハードウェアの概要 - 並列データ ウェアハウスの読み込み
ウェアハウス ソリューション Analytics Platform System (APS) で並列データ ウェアハウス (PDW) と、エンド ツー エンド データを展開するには、データ ウェアハウスをバックアップして、データの読み込みの計画を作成する必要があります。 取得して、ビジネス要件を満たすサーバーをバックアップおよび読み込みを構成するには、このガイドを使用します。  
  
## <a name="acquire-and-configure-backup-servers"></a>取得して、バックアップ サーバーを構成します。  
![バックアップ プロセス](media/backup-process.png "バックアップ プロセス")  
  
PDW のデータベースをバックアップするため、1 つまたは複数のバックアップ サーバーを作成する必要があります。 既存のハードウェアを使用したり、新しいハードウェアを購入することができます。 詳細については、次を参照してください。[取得およびサーバーのバックアップを構成](acquire-and-configure-backup-server.md)です。 この手順では、[サーバー容量の計画ワークシートをバックアップ](backup-capacity-planning-worksheet.md)バックアップに適したソリューションを計画するときにします。  
  
## <a name="acquire-and-configure-loading-servers"></a>取得し、読み込みのサーバーを構成します。  
![読み込みプロセス](media/loading-process.png "読み込みプロセス")  
  
データを読み込むには、1 つまたは複数のサーバーの読み込みが必要です。 新しいサーバーを購入することや、独自の既存の ETL または他のサーバーを使用できます。 詳細については、次を参照してください。 [Acquire 読み込み中にサーバーを構成および](acquire-and-configure-loading-server.md)です。 この手順では、[サーバー容量の計画ワークシートを読み込む](loading-server-capacity-planning-worksheet.md)を読み込み中に適したソリューションを計画します。  
  
## <a name="see-also"></a>参照  
[バックアップと復元の概要](backup-and-restore-overview.md)  
[ロードの概要](load-overview.md)  
  
