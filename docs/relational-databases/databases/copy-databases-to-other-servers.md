---
title: 他のサーバーへのデータベースのコピー | Microsoft Docs
description: SQL Server データベースをテストのために別のコンピューターにコピーする方法、それをリモートブランチ操作で使用できるようにする方法、またはその他の理由について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93f42e9234ee9cd67503c2abc70c37e309a041ea
ms.sourcegitcommit: e922721431d230c45bbfb5dc01e142abbd098344
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "82138165"
---
# <a name="copy-databases-to-other-servers"></a>他のサーバーへのデータベースのコピー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  テスト、一貫性の確認、ソフトウェアの開発、レポートの実行、ミラー データベースの作成、遠隔地の支社での運用などを目的として、データベースをコピーすることが必要になる状況があります。  
  
 データベースは、次の方法でコピーできます。  
  
-   データベース コピー ウィザードの使用  
  
     データベース コピー ウィザードを使用して、サーバー間でデータベースを移動またはコピーしたり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを新しいバージョンにアップグレードしたりすることができます。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
-   データベース バックアップの復元  
  
     データベース全体をコピーするため、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの BACKUP と RESTORE を使用できます。 通常、さまざまな理由によりデータベースを別のコンピューターにコピーする場合、データベースの完全バックアップを復元する方法を使用します。 バックアップと復元によるデータベースのコピーの詳細については、「 [バックアップと復元によるデータベースのコピー](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)」を参照してください。  
  
    > [!NOTE]  
    >  データベース ミラーリングのミラー データベースを設定するには、RESTORE DATABASE *<database_name>* WITH NORECOVERY を使用して、データベースをミラー サーバーに復元する必要があります。 詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。  
  
-   スクリプトの生成ウィザードを使用したデータベースのパブリッシュ  
  
     スクリプトの生成ウィザードを使用すると、ローカル コンピューターから Web ホスティング プロバイダーにデータベースを転送できます。 詳細については、「 [スクリプトの生成とパブリッシュ ウィザード](../../relational-databases/scripting/generate-and-publish-scripts-wizard.md)」を参照してください。  
  
  
