---
title: "スナップショット フォルダーの代替位置 | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: "36"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c1d03f6d3d20f821eeb1ab4e8930b06fc0f997e
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="alternate-snapshot-folder-locations"></a>スナップショット フォルダーの代替位置
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] スナップショットの代替位置を使用すると、既定の場所 (通常はディストリビューター上) 以外の場所、または既定の場所に加えて別の場所にスナップショット ファイルを格納できます。 代替位置には、別のサーバー、ネットワーク ドライブ、またはリムーバブル メディア (CD-ROM またはリムーバブル ディスクなど) を指定できます。  
  
 スナップショットの代替位置は、パブリケーションのプロパティとして格納されます。 スナップショットの代替位置はパブリケーション プロパティであるため、ディストリビューション エージェントおよびマージ エージェントは同期処理の過程で適切なスナップショットを見つけることができます。  
  
 代替スナップショット フォルダーを指定する必要がある場合、またはスナップショット ファイルを圧縮する必要がある場合には、パブリケーションの作成時に即座に初期スナップショットを作成せず、スナップショットの場所に関するパブリケーションのプロパティを設定してから、そのパブリケーションにスナップショット エージェントを実行してください。 初期スナップショットの作成後に代替位置を変更した場合、パブリケーションに対して生成されたすべてのスナップショットは、新しい代替位置には再配置されません。 この場合、パブリケーションの設定に応じて、マージ エージェントとディストリビューション エージェントが新しい代替位置でスナップショット ファイルを見つけることができなくなる可能性があります。  
  
> [!NOTE]  
>  (**[パブリケーション プロパティ]** ダイアログ ボックスまたは [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) を使用して、) 既定のスナップショット フォルダーと同じ場所に代替位置を指定しないでください。  
  
> [!CAUTION]  
>  WebSync と代替スナップショット フォルダーの場所を同時に使用しないでください。  
  
 **スナップショットの代替位置を指定するには**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [代替スナップショット フォルダーの場所の指定 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   レプリケーション [!INCLUDE[tsql](../../includes/tsql-md.md)] プログラミング: [スナップショットのプロパティの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>参照  
 [Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [スナップショット オプション](../../relational-databases/replication/snapshot-options.md)  
  
  
