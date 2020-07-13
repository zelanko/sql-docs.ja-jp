---
title: サーバーのスタートアップ オプションの構成 (SQL Server 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af822eb405fb66f5e91340d42fc79bef0d769fbf
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935063"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a>サーバーのスタートアップ オプションの構成 (SQL Server 構成マネージャー)
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] が起動するたびに使用するスタートアップ オプションを構成する方法について説明します。 スタートアップ オプションの一覧は、「 [データベース エンジン サービスのスタートアップ オプション](database-engine-service-startup-options.md)」を参照してください。  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
### <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、スタートアップ パラメーターをレジストリに書き込みます。 これらのパラメーターは、次回 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を起動したときに有効になります。  
  
 クラスターでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がオンラインの間にアクティブ サーバー上で変更を行う必要があり、その変更は [!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動すると有効になります。 他のノードでは、次回のフェールオーバー時にスタートアップ オプションのレジストリが更新されます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 サーバーのスタートアップ オプションの構成は、レジストリの関連エントリを変更できるユーザーのみが使用できます。 該当するユーザーは次のとおりです。  
  
-   ローカル管理者グループのメンバー。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって使用されるドメイン アカウント ( [!INCLUDE[ssDE](../../includes/ssde-md.md)] がドメイン アカウントで実行されるように構成されている場合)。  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-configure-startup-options"></a>起動オプションを設定するには  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server のサービス]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          Configuration Manager を開くには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **スタートページ**で「「sqlservermanager12.msc」 (の場合)」と入力 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、12 をより小さい数値に置き換えます。 SQLServerManager12.msc をクリックすると、構成マネージャーが開きます。 Configuration Manager をスタートページまたはタスクバーにピン留めするには、「Sqlservermanager12.msc」を右クリックし、[**ファイルの場所を開く**] をクリックします。 Windows エクスプローラーで「Sqlservermanager12.msc」を右クリックし、[**スタート画面にピン留めする**] または [**タスクバーにピン留め**する] をクリックします。  
    > -   **Windows 8**:  
    >          Configuration Manager を開くには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に「 **SQLServerManager \<version> ** 」と入力し、 `SQLServerManager12.msc` **enter**キーを押します。  
  
2.  右ペインで、**[SQL Server ***<instance_name>***]** を右クリックし、**[プロパティ]** をクリックします。  
  
3.  **[起動時のパラメーター]** タブの **[起動時のパラメーターの指定]** ボックスにパラメーターを入力し、 **[追加]** をクリックします。  
  
     たとえば、シングルユーザーモードで起動するには、[ `-m` 起動時の**パラメーターの指定**] ボックスに「」と入力し、[**追加**] をクリックします。 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をシングル ユーザー モードで再起動する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを停止してください。 そうしないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって先に接続が行われ、2 番目のユーザーとして接続できなくなる場合があります。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]を再起動します。  
  
    > [!WARNING]  
    >  シングルユーザーモードの使用が完了したら、[起動時のパラメーター] ボックスで、[ `-m` 既存の**パラメーター** ] ボックスのパラメーターを選択し、[**削除**] をクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が通常のマルチユーザー モードに戻ります。  
  
## <a name="see-also"></a>参照  
 [シングルユーザーモードでの SQL Server の開始](start-sql-server-in-single-user-mode.md)   
 [システム管理者がロックアウトされた場合に SQL Server に接続する](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
