---
title: "SCM サービス - 使用されたアカウントのパスワードを変更する | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fb2daae1f2e891dbf51c096793bb493cea67f9d4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---change-the-password-of-the-accounts-used"></a>SCM サービス - 使用されたアカウントのパスワードを変更する
  このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] エージェントによって使用されるアカウントのパスワードを変更する方法について説明します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、セットアップ時に最初に指定される資格情報を使用して、コンピューター上でサービスとして実行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがドメイン アカウントで実行されていて、そのアカウントのパスワードが変更された場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されているパスワードを新しいパスワードに更新する必要があります。 パスワードを更新しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は一部のドメイン リソースにアクセスできなくなる可能性があります。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が停止すると、パスワードを更新するまでサービスが再開されません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のパスワードを変更するには、「 [[パスワードの有効期限が切れました]](http://msdn.microsoft.com/library/9831b194-9ad5-47b0-8009-59c7aef4319b)」を参照してください。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの設定を変更するように設計および承認されたツールです。 Windows サービス コントロール マネージャー ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.msc**) アプリケーションを使用して**サービスを変更すると、必要なすべての設定が変更されず、サービスが適切に機能しない場合があります。 ただし、クラスター環境では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用してアクティブ ノードのパスワードを変更した後、サービス コントロール マネージャーを使用してパッシブ ノードでパスワードを変更する必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 サービスで使用されるパスワードを変更するには、コンピューターの管理者である必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a>SQL Server (データベース エンジン) サービスで使用されるパスワードを変更するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、 **スタート画面**で、「SQLServerManager13.msc」( [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]の場合) と入力します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、13 をより小さい数値に置き換えます。 SQLServerManager13.msc をクリックすると、構成マネージャーが開きます。 スタート画面やタスク バーに構成マネージャーをピン留めするには、SQLServerManager13.msc を右クリックして、 **[ファイルの場所を開く]**をクリックします。 エクスプローラーでは、SQLServerManager13.msc を右クリックし、 **[スタート画面にピン留め]** または **[タスクバーにピン留め]**をクリックします。  
    > -   **Windows 8**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、**検索**チャームの **[アプリ]** で、「**SQLServerManager\<バージョン>.msc**」(「**SQLServerManager13.msc**」など) と入力し、**Enter** キーを押します。  
  
2.  SQL Server 構成マネージャーで **[SQL Server のサービス]**をクリックします。  
  
3.  詳細ペインで **[SQL Server (**\<instancename>**)]** を右クリックし、**[プロパティ]** をクリックします。  
  
4.  **[SQL Server (**\<instancename>**) のプロパティ]** ダイアログ ボックスの [ログオン] タブで、**[アカウント名]** ボックスに表示されるアカウントの新しいパスワードを **[パスワード]** ボックスと **[パスワードの確認入力]** ボックスに入力して、**[OK]** をクリックします。  
  
     パスワードは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動しなくてもすぐに有効になります。  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a>SQL Server エージェント サービスで使用されるパスワードを変更するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
2.  SQL Server 構成マネージャーで **[SQL Server のサービス]**をクリックします。  
  
3.  詳細ペインで **[SQL Server エージェント (**\<instancename>**)]** を右クリックし、**[プロパティ]** をクリックします。  
  
4.  **[SQL Server エージェント (**\<instancename>**) のプロパティ]** ダイアログ ボックスの [ログオン] タブで、**[アカウント名]** ボックスに表示されるアカウントの新しいパスワードを **[パスワード]** ボックスと **[パスワードの確認入力]** ボックスに入力して、**[OK]** をクリックします。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスタンドアロン インスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動しなくてもパスワードがすぐに有効になります。 クラスター インスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースをオフラインにする場合があり、再起動が必要になります。  
  
## <a name="see-also"></a>参照  
 [サービスの管理方法に関するトピック &#40;SQL Server 構成マネージャー&#41;](http://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6)  
  
  

