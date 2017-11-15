---
title: "SQL Server データベース エンジンのインストール | Microsoft Docs"
ms.custom: 
ms.date: 09/05/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
caps.latest.revision: "45"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 1beac734329cbe2f63a608a4b9482eab74a33b63
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="install-sql-server-database-engine"></a>SQL Server データベース エンジンのインストール
[!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、データの保存、処理、セキュリティ保護のためのコア サービスです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、企業において最もデータ処理量の多いアプリケーションの要求を満たすアクセス制御と高速トランザクション処理を提供します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、1 台のコンピューターで最大 50 個の [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスをサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の標準的なインストール方法については、「[SQL Server をインストール ウィザードからインストールする &#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)」を参照してください。  
  
>[!IMPORTANT]
>ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。  
  
## <a name="related-features"></a>関連機能

**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの [インストールするコンポーネント] ページで** データベース エンジン [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択すると、次の機能がインストールされます。  
  
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
>  既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にサンプル データベースとサンプル コードはインストールされません。 サンプル データベースとサンプルをインストールする場合は、「[Microsoft SQL Server のサンプル](../../sample/microsoft-sql-server-samples.md)」を参照してください。 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843) で古いサンプルを参照してください。  
  
## <a name="see-also"></a>参照  
 [エディションと SQL Server 2017 のサポートされる機能](~/sql-server/editions-and-components-of-sql-server-2017.md)   
 [SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [高可用性ソリューション &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [インストール ウィザードを使用した SQL Server のアップグレード &#40;セットアップ&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
