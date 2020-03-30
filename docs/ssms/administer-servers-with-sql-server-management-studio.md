---
title: SQL Server Management Studio によるサーバー管理
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: markingmyname
ms.author: maghan
ms.openlocfilehash: fdf38619102dde1ecf5b8e92f70ec2ea79c77811
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254531"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>SQL Server Management Studio によるサーバー管理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と Azure SQL Database の管理者のサーバー管理要件を満たすように設計された、優れた統合管理クライアントです。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]では、オブジェクト エクスプローラーを使用して管理タスクを実行します。オブジェクト エクスプローラーでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ファミリのあらゆるサーバーに接続して、その内容をグラフィカルに表示できます。 対象になるサーバーは、 [!INCLUDE[ssDE](../includes/ssde_md.md)]、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)]、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 、Azure SQL Database のインスタンスです。  
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] のツール コンポーネントとしては、登録済みサーバー、オブジェクト エクスプローラー、ソリューション エクスプローラー、テンプレート エクスプローラー、[オブジェクト エクスプローラーの詳細] ページ、ドキュメント ウィンドウがあります。 ツールを表示するには、 **[表示]** メニューでツール名をクリックします。 クエリ エディター ツールを表示するには、ツール バーの **[新しいクエリ]** ボタンをクリックします。  
  
> [!IMPORTANT]  
> 既定では、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] と [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の間のネットワーク通信は暗号化されません。 暗号化接続を確立しない限り、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ではパスワードなどの機密データを処理しないでください。 詳細については、「 [データベース エンジンへの暗号化接続の有効化方法 (SQL Server Configuration Manager)](https://msdn.microsoft.com/e1e55519-97ec-4404-81ef-881da3b42006)」を参照してください。  
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] を使用して以下の操作を実行できます。  
  
-   サーバーの登録  
  
-   [!INCLUDE[ssDE](../includes/ssde_md.md)]、SSAS、[!INCLUDE[ssRS](../includes/ssrs.md)]、[!INCLUDE[ssIS](../includes/ssis_md.md)]、または Azure SQL Database のインスタンスへの接続  
  
-   サーバー プロパティの設定  
  
-   データベースや SSAS オブジェクト (キューブ、ディメンション、アセンブリなど) の管理  
  
-   オブジェクト (データベース、テーブル、キューブ、データベース ユーザー、ログインなど) の作成  
  
-   ファイルとファイル グループの管理  
  
-   データベースのインポート/デタッチ  
  
-   スクリプト ツールの起動  
  
-   セキュリティの管理  
  
-   システム ログの表示  
  
-   現在の利用状況の監視  
  
-   レプリケーションの設定  
  
-   フルテキスト インデックスの管理  
  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントの開始と停止には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用します。  
  
## <a name="see-also"></a>参照  
[SQL Server Management Studio の使用 [SQL Server]](../ssms/use-sql-server-management-studio.md)  
[サーバーのプロパティを表示する方法 (SQL Server Management Studio)](https://msdn.microsoft.com/55f3ac04-5626-4ad2-96bd-a1f1b079659d)  
  
