---
title: "DQS セキュリティ | Microsoft Docs"
ms.custom: 
ms.date: 10/01/2012
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: data-quality-services
ms.reviewer: 
ms.suite: sql
ms.technology: data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c8783392c318700bd5cc7c4e9db02f086741b098
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="dqs-security"></a>DQS セキュリティ
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のセキュリティ インフラストラクチャは、SQL Server のセキュリティ インフラストラクチャに基づいています。 データベース管理者は、ユーザーに DQS ロールを関連付けることによって、ユーザーに一連の権限を付与します。 これにより、ユーザーがアクセスできる DQS リソースや、ユーザーが実行できる機能アクティビティを定義します。  
  
## <a name="dqs-roles"></a>DQS ロール  
 DQS には 4 つのロールがあります。 1 つはデータベース管理者 (DBA) で、主に製品のインストール、データベースのメンテナンス、およびユーザー管理を行います。 このロールは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションよりも SQL Server Management Studio を主に使用します。 このサーバー ロールは sysadmin です。  
  
 その他の 3 つのロールは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションを使用して製品を直接使用するインフォメーション ワーカー、データ スチュワード用です。 これらのロールには、次が含まれます。  
  
-   **DQS 管理者** (dqs_administrator ロール) は、製品のスコープ内のすべてを行うことができます。 管理者は、プロジェクトの編集と実行、ナレッジ ベースの作成と編集、アクティビティの終了、アクティビティ内のプロセスの停止、および構成と参照データ サービス設定の変更を行うことができます。 ただし、DQS 管理者は、サーバーのインストールや新しいユーザーの追加はできません。 これらはデータベース管理者が行う必要があります。  
  
-   **DQS KB エディター** (dqs_kb_editor ロール) は、管理を除いて DQS アクティビティのすべてを実行できます。 KB エディターは、プロジェクトの編集と実行、およびナレッジ ベースの作成と編集を行うことができます。 アクティビティ監視データを参照することはできますが、アクティビティの終了や停止、または管理業務の実行はできません。  
  
-   **DQS KB オペレーター** (dqs_kb_operator ロール) は、プロジェクトの編集や実行を行うことができます。 どのようなナレッジ マネージメントも実行できず、ナレッジ ベースの作成や変更もできません。 アクティビティ監視データを参照することはできますが、アクティビティの終了または管理業務の実行はできません。  
  
## <a name="user-management"></a>ユーザー管理  
 データベース管理者 (DBA) は DQS ユーザーを作成し、SQL Server Management Studio の DQS ロールに関連付けます。 DBA は、DQS_MAIN データベースのユーザーとして SQL ログインを追加し、各ユーザーを DQS ロールの 1 つと関連付けることによってユーザーの権限を管理します。 各ロールには、DQS_MAIN データベースの一連のストアド プロシージャに対する権限が付与されています。 DQS_PROJECTS および DQS_STAGING_DATA データベースについては、3 つの DQS ロールは使用できません。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|SQL Server Management Studio を使用してユーザーを作成し、DQS ロールを付与する方法について説明します。|[SSMS による DQS ユーザーの管理](http://msdn.microsoft.com/library/955af01d-00da-4c51-9311-f3848749df54)|  
  
  
