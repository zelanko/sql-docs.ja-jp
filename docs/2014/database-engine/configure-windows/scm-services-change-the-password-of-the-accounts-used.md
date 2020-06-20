---
title: SQL Server によって使用されるアカウントのパスワードを変更する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1454e29835c0087fb75c93a1680f452dfe0f2c05
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935086"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a>SQL Server で使用されるアカウントのパスワードの変更 (SQL Server 構成マネージャー)
  このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] エージェントによって使用されるアカウントのパスワードを変更する方法について説明します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、セットアップ時に最初に指定される資格情報を使用して、コンピューター上でサービスとして実行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがドメイン アカウントで実行されていて、そのアカウントのパスワードが変更された場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されているパスワードを新しいパスワードに更新する必要があります。 パスワードを更新しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は一部のドメイン リソースにアクセスできなくなる可能性があります。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が停止すると、パスワードを更新するまでサービスが再開されません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のパスワードを変更するには、「 [[パスワードの有効期限が切れました]](../password-expired.md)」を参照してください。  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの設定を変更するように設計および承認されたツールです。 Windows サービス コントロール マネージャー ( **services.msc** ) アプリケーションを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスを変更すると、必要なすべての設定が変更されず、サービスが適切に機能しない場合があります。 ただし、クラスター環境では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用してアクティブ ノードのパスワードを変更した後、サービス コントロール マネージャーを使用してパッシブ ノードでパスワードを変更する必要があります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 サービスで使用されるパスワードを変更するには、コンピューターの管理者である必要があります。  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a>SQL Server (データベース エンジン) サービスで使用されるパスワードを変更するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          Configuration Manager を開くには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **スタートページ**で「「sqlservermanager12.msc」 (の場合)」と入力 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、12 をより小さい数値に置き換えます。 SQLServerManager12.msc をクリックすると、構成マネージャーが開きます。 Configuration Manager をスタートページまたはタスクバーにピン留めするには、「Sqlservermanager12.msc」を右クリックし、[**ファイルの場所を開く**] をクリックします。 Windows エクスプローラーで「Sqlservermanager12.msc」を右クリックし、[**スタート画面にピン留めする**] または [**タスクバーにピン留め**する] をクリックします。  
    > -   **Windows 8**:  
    >          Configuration Manager を開くには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に「 **SQLServerManager \<version> ** 」と入力し、 `SQLServerManager12.msc` **enter**キーを押します。  
  
2.  SQL Server 構成マネージャーで **[SQL Server のサービス]** をクリックします。  
  
3.  詳細ウィンドウで、[ **SQL Server (**)] を右クリックし、[ \<instancename> **)****プロパティ**] をクリックします。  
  
4.  [ **SQL Server (** \<instancename> **) のプロパティ**] ダイアログボックスの [ログオン] タブで、[**アカウント名**] ボックスに表示されているアカウントの新しいパスワードを [**パスワード**] ボックスと [**パスワードの確認**入力] ボックスに入力し、[ **OK**] をクリックします。  
  
     パスワードは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動しなくてもすぐに有効になります。  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a>SQL Server エージェント サービスで使用されるパスワードを変更するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
2.  SQL Server 構成マネージャーで **[SQL Server のサービス]** をクリックします。  
  
3.  詳細ウィンドウで、[ **SQL Server エージェント (**)] を右クリックし、[ \<instancename> **)****プロパティ**] をクリックします。  
  
4.  [ **SQL Server エージェント (** \<instancename> **) のプロパティ**] ダイアログボックスの [ログオン] タブで、[**アカウント名**] ボックスに表示されているアカウントの新しいパスワードを [**パスワード**] ボックスと [**パスワードの確認**入力] ボックスに入力し、[ **OK**] をクリックします。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスタンドアロン インスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動しなくてもパスワードがすぐに有効になります。 クラスター インスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースをオフラインにする場合があり、再起動が必要になります。  
  
## <a name="see-also"></a>参照  
 [サービスの管理方法に関するトピック &#40;SQL Server 構成マネージャー&#41;](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
