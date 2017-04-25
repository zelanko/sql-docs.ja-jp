---
title: "SQL Server Management Studio - リリース ノート | Microsoft Docs"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b95337b-80bf-4624-8f5d-cdaf6181d3b8
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51e336a22d0c1052c48b8e569330aef26f2af094
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-management-studio----release-notes"></a>SQL Server Management Studio - リリース ノート
SQL Server Management Studio の一般公開版リリースにようこそ!  このリリースの SQL Server Management Studio (SSMS) は SQL Server リリースとは別の、スタンドアロン インストールです。 目的は、新しい機能、修正プログラム、SQL Server と Azure SQL Database の最新機能に対するサポートで頻繁に更新することです。  
  
最新の SQL Server Management Studio をインストールするには、「[SQL Server Management Studio &#40;SSMS&#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)」をご覧ください。  
  
このリリースの SQL Server Management Studio に関連する問題と制約を次に示します。  

1. **Active Directory ユニバーサル認証を使用して SSMS インスタンス用にログインできる Azure Active Directory アカウントは 1 つだけです。**  
    この制限は、Active Directory ユニバーサル認証に限定されます。Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証を使用して別のサーバーにログインできます。
    
    回避策としては、別の SSMS インスタンスを使用して、別の Azure Active Directory アカウントとしてログインしてください。 
    
2. **SSMS でのデータ層アプリケーション フレームワーク (DacFx) コマンドおよびスキーマ デザイナーでは、Active Directory ユニバーサル認証はサポートされていません。**  
    SSMS での DacFx を使用するコマンド (例: インポートおよびエクスポート) 、 スキーマ デザイナーでは、現在 Active Directory ユニバーサル認証はサポートされていません。
    
    回避策としては、Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証など、SSMS で提供される認証の他の形式を使用してください。

3. **SSMS は SQL Server 2016 Integrated Services (SSIS 2016) インスタンスしか接続できません。**  
    以前のバージョンに接続できない SQL Server Integration Services との互換性に関する既知の制限があります。
    
    この問題の回避策としては、 [SSIS インスタンスと連携された SSMS リリース](../ssms/previous-sql-server-management-studio-releases.md)を使用して、SQL Server Integration Service インスタンスに接続してください。 
  
4. **SSMS は、SQL Server 2008 R2 と以前の SQL Server のバージョンのメンテナンス プランを保存しません。**  
    これは将来に対応する既知の制限です。 それまでは、 [SSMS 2014 リリース](../ssms/previous-sql-server-management-studio-releases.md) を使用して、メンテナンス プランを保存してください。  
    
5. **英語以外の SSMS のインストールには、追加のセキュリティ パッケージのインストールが必要になる場合があります。**  
SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。
  
6. **SQL Server 構成マネージャーは、SQL Server がクライアント コンピューターにインストールされていない場合は起動できません。**  
    SQL server がクライアント コンピューターにインストールされておらず、SQL Server 構成マネージャーを起動する場合は、次のエラーが表示されます。   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * SQL Server インスタンスを SSMS の ’登録済みサーバー’ 一覧に追加している場合は、次の手順に従います。  
        1. SSMS の '登録済みサーバー’ ビューに移動します。  
        2. 構成する SQL Server インスタンスを右クリックします。  
        3. 右クリックで表示されるメニューで、'SQL Server 構成マネージャー...' を選択します 。    
          
      * SQL Server インスタンスを SSMS の ’登録済みサーバー’ 一覧に追加していない場合は、次の手順に従います。  
        1. 管理者としてコマンド プロンプトを開きます。  
        2. 次のコマンドを使用して、Mofcomp ツールを実行します。  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Mofcomp ツールを実行した後、次のコマンドを実行して、WMI サービスを再起動し、変更を有効にします。  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

## <a name="feedback"></a>フィードバック  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Microsoft Connect で問題や提案を記録](https://connect.microsoft.com/SQLServer/Feedback)。  
  
## <a name="see-also"></a>参照  
[SQL Server Management Studio のチュートリアル](../ssms/use-sql-server-management-studio.md)  
[SQL Server Management Studio &amp;#40;SSMS&amp;#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  
[SQL Server Management Studio の以前のリリース](../ssms/previous-sql-server-management-studio-releases.md)  

  

