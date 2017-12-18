---
title: "他のサーバーへのデータベースのコピー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
caps.latest.revision: "42"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4f3b75305cf6db462e099d1a2a752bbca6014826
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="copy-databases-to-other-servers"></a>他のサーバーへのデータベースのコピー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] テスト、一貫性の確認、ソフトウェアの開発、レポートの実行、ミラー データベースの作成、遠隔地の支社での運用などを目的として、データベースをコピーすることが必要になる状況があります。  
  
 データベースは、次の方法でコピーできます。  
  
-   データベース コピー ウィザードの使用  
  
     データベース コピー ウィザードを使用して、サーバー間でデータベースを移動またはコピーしたり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを新しいバージョンにアップグレードしたりすることができます。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
-   データベース バックアップの復元  
  
     データベース全体をコピーするため、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの BACKUP と RESTORE を使用できます。 通常、さまざまな理由によりデータベースを別のコンピューターにコピーする場合、データベースの完全バックアップを復元する方法を使用します。 バックアップと復元によるデータベースのコピーの詳細については、「[バックアップと復元によるデータベースのコピー](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)」を参照してください。  
  
    > [!NOTE]  
    >  データベース ミラーリングのミラー データベースを設定するには、RESTORE DATABASE *<database_name>* WITH NORECOVERY を使用して、データベースをミラー サーバーに復元する必要があります。 詳細については、「[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)」を参照してください。  
  
-   スクリプトの生成ウィザードを使用したデータベースのパブリッシュ  
  
     スクリプトの生成ウィザードを使用すると、ローカル コンピューターから Web ホスティング プロバイダーにデータベースを転送できます。 詳細については、「 [スクリプトの生成とパブリッシュ ウィザード](../../relational-databases/scripting/generate-and-publish-scripts-wizard.md)」を参照してください。  
  
  
