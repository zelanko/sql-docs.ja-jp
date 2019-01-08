---
title: SQL Server Backup and Restore with Windows Azure Blob ストレージ サービス |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6a0c9b6a-cf71-4311-82f2-12c445f63935
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 52f1bdf9e748625e1310210c98beeb4401a5dd81
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353149"
---
# <a name="sql-server-backup-and-restore-with-windows-azure-blob-storage-service"></a>Windows Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元
  このトピックでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびへのバックアップから復元する、 [Windows Azure Blob ストレージ サービス](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)します。 また、Windows Azure BLOB Service を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップを格納する利点の概要についても説明します。  
  
 SQL Server では、次の方法で Windows Azure Blob ストレージ サービスにバックアップを格納できます。  
  
-   **Windows Azure へのバックアップを管理するには。** 使用する同じメソッドを使用してディスクとテープへのバックアップ、今すぐバックアップできます Windows Azure ストレージにバックアップ先として URL を指定することによって。  この機能を使用すると、手動でバックアップすることも、ローカル ストレージまたはその他のオフサイト オプションの場合と同じように独自のバックアップ方法を構成することもできます。 この機能は、 **SQL Server Backup to URL**とも呼ばれます。 詳細については、「 [SQL Server Backup to URL](sql-server-backup-to-url.md)」を参照してください。 この機能は、SQL Server 2012 SP1 CU2 以降で使用できます。  
  
    > [!NOTE]  
    >  SQL Server 2014 より前の SQL Server バージョンでは、Windows Azure への SQL Server バックアップ ツール アドインを使用して、Windows Azure ストレージへのバックアップをすばやく簡単に作成できます。 詳細については、 [ダウンロード センター](https://go.microsoft.com/fwlink/?LinkID=324399)を参照してください。  
  
-   **Windows Azure へのバックアップの SQL Server 管理できるようにします。** SQL Server の 1 つのデータベースまたは複数データベースのバックアップ方法やスケジュールを管理したり、インスタンス レベルで既定値の設定を構成します。 この機能と呼ばれます **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]** します。 詳細については、次を参照してください。 [SQL Server Managed Backup to Windows Azure](sql-server-managed-backup-to-microsoft-azure.md)します。 この機能は、SQL Server 2014 以降で使用できます。  
  
## <a name="benefits-of-using-the-windows-azure-blob-service-for-includessnoversionincludesssnoversion-mdmd-backups"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップに Windows Azure BLOB サービスを使用する利点  
  
-   柔軟で信頼性が高く、制限のないオフサイト ストレージ:Windows Azure BLOB Service へのバックアップの保存は、アクセスしやすく便利で柔軟なオフサイトのオプションです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ用にオフサイト ストレージを作成するのは、既存のスクリプトやジョブを変更するのと同様に簡単です。 オフサイト ストレージは、通常、災害発生時にオフサイトと運用データベース両方の場所に影響しないように、運用データベースの場所から十分に離れた場所に設置する必要があります。 BLOB ストレージを地理的に離れた場所にレプリケートすることによって、地域全体に影響する可能性がある災害が発生した場合の保護レベルが強化されます。 また、バックアップは場所や時間を問わず使用でき、復元のために簡単にアクセスできます。  
  
-   バックアップ アーカイブ:Windows Azure Blob ストレージ サービスでは、バックアップをアーカイブによく使用されるテープ オプションに代替を提供します。 テープ ストレージでは、オフサイトの施設への物理的な輸送手段とメディアを保護する手段が必要になります。 Windows Azure BLOB ストレージへのバックアップ保存は、すぐに使用でき、可用性が高く、持続性を備えたアーカイブ オプションです。  
  
-   ハードウェア管理のオーバーヘッドなし: Windows Azure サービスを使用したハードウェア管理にはオーバーヘッドが生じません。 Windows Azure サービスでは、ハードウェアが管理され、ハードウェア障害に対する冗長性と保護を目的として地理的に離れた場所へのレプリケーションが提供されます。  
  
-   現在、Windows Azure 仮想マシンで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスでは、アタッチされたディスクを作成することで、Windows Azure BLOB ストレージ サービスへのバックアップを実行できます。 ただし、Windows Azure バーチャル マシンにアタッチできるディスク数には制限があります。 ディスク数の上限は、XL インスタンスでは 16 台、サイズの小さいインスタンスではこれより少なくなります。 Windows Azure BLOB ストレージに直接バックアップできるようにすることで、16 台のディスク制限がなくなります。  
  
     また、Windows Azure BLOB ストレージ サービスに保存されているバックアップ ファイルは、内部設置型の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、または Windows Azure バーチャル マシンで実行している別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で直接使用できます。その際、データベースのアタッチ/デタッチや、VHD のダウンロードとアタッチは必要ありません。  
  
-   コスト面での利点:使用するサービスにのみ料金がかかります。 オフサイトのバックアップ アーカイブ オプションとして、優れたコスト効果を得ることができます。 参照してください、 [Windows Azure の課金に関する注意点](#Billing)セクションの詳細情報とリンクします。  
  
##  <a name="Billing"></a> Windows Azure の課金に関する注意点:  
 Windows Azure ストレージのコストを把握しておくと、Windows Azure でバックアップを作成および格納するコストを予測できます。  
  
 [Windows Azure 料金計算ツール](https://go.microsoft.com/fwlink/?LinkId=277060)コストを見積もることができます。  
  
 **記憶域:** 料金は、使用領域に基づいており、段階的なスケールと冗長性のレベルで計算されます。 詳細と最新情報については、「 **料金の詳細** 」の「 [データ管理](https://go.microsoft.com/fwlink/?LinkId=277059) 」を参照してください。  
  
 **データ転送:** Windows Azure への受信データ転送は無料です。 送信転送は、帯域幅の使用量に対して課金され、段階的な地域固有の区分に基づいて計算されます。 詳細については、「 [料金の詳細](https://go.microsoft.com/fwlink/?LinkId=277061) 」の「データ転送」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [システム データベースのバックアップと復元 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [チュートリアル:SQL Server のバックアップと Windows Azure Blob ストレージ サービスへの復元](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [SQL Server Backup to URL](sql-server-backup-to-url.md)  
  
  
