---
title: "データベース エンジンのアップグレードの完了 | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 581e8cd7a43dd1e4c878cc56b49644e51d7a3a79
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="complete-the-database-engine-upgrade"></a>データベース エンジンのアップグレードの完了

SQL Server へのアップグレードが完了したら、必要に応じて追加の手順をいくつか実行する必要があります。 その一部を次に示します。  
  
[!INCLUDE[ssDE](../../includes/ssde-md.md)]をアップグレードした後は、次の作業を実行します。  
  
- **データベースのバックアップ:** 各データベースの完全バックアップを実行します。  

- **新機能の有効化:** SQL Server 2016 および SQL Server 2017 では、一部の変更は、データベースの DATABASE_COMPATIBILITY レベルが 130 以上に変更された後に有効になります。  詳細と推奨ワークフローについては、「 [データベース互換性モードの変更とクエリ ストアの使用](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md)」を参照してください。  
  
- **Integration Services:**  
  
     Integration Services パッケージを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 形式に移行します。 詳細については、「 [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md)」を参照してください。  
  
- **Reporting Services:** 新しいインストールのアップグレードの場合は、Reporting Services の暗号化キーを復元します。 詳細については、「 [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)」を参照してください。  
  
- **マスター データ サービス:** MDS データベース スキーマをアップグレードし、SQL Server 2017 の Web アプリケーションを作成します。 詳細については、「 [Upgrade Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md)」を参照してください。  
  
- **Data Quality Services:** DQS データベース スキーマをアップグレードし、DQS データベース スキーマのアップグレードを確認します。 詳細については、「 [Upgrade Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md)」を参照してください。  
  
- **フルテキスト検索:** クエリ結果のセマンティクスの一貫性を維持するために、フルテキスト カタログを再作成します。 詳細については、「 [フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)」をご覧ください。  
  

