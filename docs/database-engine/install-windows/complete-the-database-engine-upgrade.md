---
title: "データベース エンジンのアップグレードの完了 | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# データベース エンジンのアップグレードの完了
  SQL Server 2016 へのアップグレードが完了したら、必要に応じて追加の手順をいくつか実行する必要があります。 その一部を次に示します。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]をアップグレードした後は、次の作業を実行します。  
  
-   **データベースのバックアップ:** アップグレードした各データベースの完全バックアップを実行します。  
  
-   **新機能の有効化:** SQL Server 2016 では、一部の変更は、データベースの DATABASE_COMPATIBILITY レベルが 130 に変更された後に有効になります。  詳細と推奨ワークフローについては、「[データベース互換性モードの変更とクエリ ストアの使用](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md)」を参照してください。  
  
-   **Integration Services:**  
  
     Integration Services パッケージを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 形式に移行します。 詳細については、「 [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md)」を参照してください。  
  
-   **Reporting Services:** 新しいインストールのアップグレードの場合は、Reporting Services の暗号化キーを復元します。 詳細については、「 [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md)」を参照してください。  
  
-   **マスター データ サービス:**  MDS データベース スキーマをアップグレードし、SQL Server 2016 の Web アプリケーションを作成します。 詳細については、「 [Upgrade Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md)」を参照してください。  
  
-   **Data Quality Services:** DQS データベース スキーマをアップグレードし、DQS データベース スキーマのアップグレードを確認します。 詳細については、「 [Upgrade Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md)」を参照してください。  
  
-   **フルテキスト検索:** クエリ結果のセマンティクスの一貫性を維持するために、フルテキスト カタログを再作成します。 詳細については、「[フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)」を参照してください。  
  
## この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。  [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Complete%20the%20Database%20Engine%20Upgrade%20page)にコメントをお送りください。  
  
  