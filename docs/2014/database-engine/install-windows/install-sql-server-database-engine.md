---
title: SQL Server データベースエンジン | についてMicrosoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3cf4ca5d422e9d124c397bbcae8d8b48d12b95b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932733"
---
# <a name="about-the-sql-server-database-engine"></a>SQL Server データベース エンジンについて
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、データの保存、処理、セキュリティ保護のためのコア サービスです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、企業において最もデータ処理量の多いアプリケーションの要求を満たすアクセス制御と高速トランザクション処理を提供します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、1 台のコンピューターで最大 50 個の [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスをサポートします。 一般的なインストールを作成するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「インストール[ウィザードから SQL Server 2014 をインストールする」 &#40;セットアップ&#41;](install-sql-server-from-the-installation-wizard-setup.md)を参照してください。  
  
 **重要** ローカルでのインストールの場合、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。  
  
 インストールウィザードの [インストールするコンポーネント] ページで [ ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースエンジン**] を選択すると、次の機能がインストールされ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   レプリケーション (オプションのコンポーネント)  
  
-   フルテキスト検索 (オプションのコンポーネント)  
  
-   Data Quality Services (オプションのコンポーネント)  
  
    > [!NOTE]  
    >  今回のリリースでは、セットアップで **[Data Quality Services]** チェック ボックスをオンにしても、Data Quality Services (DQS) サーバーはインストールされません。 DQS サーバーをインストールするには、インストール後の追加の手順を実行する必要があります。 詳細については、「 [Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)」を参照してください。  
  
 一般的なユーザー シナリオでは、データベース サービスに加えて次の機能もインストールします。  
  
-   Data Quality クライアント  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   接続コンポーネント  
  
-   プログラミング モデル  
  
-   管理ツール  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Documentation コンポーネント  
  
> [!NOTE]  
>  既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にサンプル データベースとサンプル コードはインストールされません。 サンプル データベースとサンプル コードをインストールする場合は、 [CodePlex Web サイト](https://go.microsoft.com/fwlink/?LinkId=87843)を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [SQL Server 2014 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [SQL Server インストールの計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [高可用性ソリューション &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [インストールウィザード &#40;セットアップを使用して SQL Server 2014 にアップグレード&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
