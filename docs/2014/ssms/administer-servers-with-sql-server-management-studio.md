---
title: SQL Server Management Studio によるサーバー管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6dabef37d796ca1279c1444cf6ecafce6973c86b
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "40396271"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>SQL Server Management Studio によるサーバー管理
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 優れた統合管理のクライアントが満たすために設計されていますが、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]管理者のサーバー管理要件。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]では、オブジェクト エクスプローラーを使用して管理タスクを実行します。オブジェクト エクスプローラーでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ファミリのあらゆるサーバーに接続して、その内容をグラフィカルに表示できます。 対象になるサーバーは、[!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、または [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のインスタンスです。  
  
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] のツール コンポーネントとしては、登録済みサーバー、オブジェクト エクスプローラー、ソリューション エクスプローラー、テンプレート エクスプローラー、[オブジェクト エクスプローラーの詳細] ページ、ドキュメント ウィンドウがあります。 ツールを表示するには、 **[表示]** メニューでツール名をクリックします。 クエリ エディター ツールを表示するには、ツール バーの **[新しいクエリ]** ボタンをクリックします。  
  
> [!IMPORTANT]  
>  既定では、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] と [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の間のネットワーク通信は暗号化されません。 暗号化接続を確立しない限り、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ではパスワードなどの機密データを処理しないでください。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] を使用して以下の操作を実行できます。  
  
-   サーバーの登録  
  
-   [!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssAS](../includes/ssas-md.md)]、[!INCLUDE[ssRS](../includes/ssrs.md)]、または [!INCLUDE[ssIS](../includes/ssis-md.md)] のインスタンスへの接続  
  
-   サーバー プロパティの設定  
  
-   データベースや [!INCLUDE[ssAS](../includes/ssas-md.md)] オブジェクト (キューブ、ディメンション、アセンブリなど) の管理  
  
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
 [SQL Server Management Studio の使用 [SQL Server]](../database-engine/use-sql-server-management-studio.md)   
 [サーバー プロパティの表示または変更 &#40;SQL Server&#41;](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
