---
title: "SQL Server Management Studio によるサーバー管理 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d73b15b799fe8c52124331cfc346d3759fc860a6
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="administer-servers-with-sql-server-management-studio"></a>SQL Server Management Studio によるサーバー管理
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] と Azure SQL Database の管理者のサーバー管理要件を満たすように設計された、優れた統合管理クライアントです。 [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)]では、オブジェクト エクスプローラーを使用して管理タスクを実行します。オブジェクト エクスプローラーでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] ファミリのあらゆるサーバーに接続して、その内容をグラフィカルに表示できます。 対象になるサーバーは、 [!INCLUDE[ssDE](../includes/ssde_md.md)]、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)]、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)]、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] 、Azure SQL Database のインスタンスです。  
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] のツール コンポーネントとしては、登録済みサーバー、オブジェクト エクスプローラー、ソリューション エクスプローラー、テンプレート エクスプローラー、[オブジェクト エクスプローラーの詳細] ページ、ドキュメント ウィンドウがあります。 ツールを表示するには、 **[表示]** メニューでツール名をクリックします。 クエリ エディター ツールを表示するには、ツール バーの **[新しいクエリ]** ボタンをクリックします。  
  
> [!IMPORTANT]  
> 既定では、 [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] と [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] の間のネットワーク通信は暗号化されません。 暗号化接続を確立しない限り、 [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] ではパスワードなどの機密データを処理しないでください。 詳細については、「 [データベース エンジンへの暗号化接続の有効化方法 (SQL Server Configuration Manager)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006)」を参照してください。  
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] を使用して以下の操作を実行できます。  
  
-   サーバーの登録  
  
-   [!INCLUDE[ssDE](../includes/ssde_md.md)]、 [!INCLUDE[ssAS](../includes/ssas_md.md)]、 [!INCLUDE[ssRS](../includes/ssrs_md.md)]、  [!INCLUDE[ssIS](../includes/ssis_md.md)] 、Azure SQL Database のインスタンスへの接続  
  
-   サーバー プロパティの設定  
  
-   データベースや [!INCLUDE[ssAS](../includes/ssas_md.md)] オブジェクト (キューブ、ディメンション、アセンブリなど) の管理  
  
-   オブジェクト (データベース、テーブル、キューブ、データベース ユーザー、ログインなど) の作成  
  
-   ファイルとファイル グループの管理  
  
-   データベースのインポート/デタッチ  
  
-   スクリプト ツールの起動  
  
-   セキュリティの管理  
  
-   システム ログの表示  
  
-   現在の利用状況の監視  
  
-   レプリケーションの設定  
  
-   フルテキスト インデックスの管理  
  
[!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] または [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] エージェントの開始と停止には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] 構成マネージャーを使用します。  
  
## <a name="see-also"></a>参照  
[SQL Server Management Studio の使用 [SQL Server]](../ssms/use-sql-server-management-studio.md)  
[サーバーのプロパティを表示する方法 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/55f3ac04-5626-4ad2-96bd-a1f1b079659d)  
  

