---
title: コマンド プロンプトから PowerPivot のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e6da1b23bd23634e3edb8d92093cab6ce71a2783
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094558"
---
# <a name="install-powerpivot-from-the-command-prompt"></a>コマンド プロンプトからの PowerPivot のインストール
  コマンド ラインからセットアップを実行して、SQL Server PowerPivot for SharePoint をインストールすることができます。 コマンドには `/ROLE` パラメーターを含め、`/FEATURES` パラメーターを除外する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 SharePoint Server 2010 Enterprise Edition Service Pack 1 (SP1) をインストールする必要があります。  
  
 Analysis Services を準備するには、ドメイン アカウントを使用する必要があります。  
  
 コンピューターが SharePoint ファームと同じドメインに参加する必要があります。  
  
##  <a name="Commands"></a> /ROLE に基づくインストール オプション  
 PowerPivot for SharePoint の配置では `/ROLE` パラメーターの代わりに `/FEATURES` パラメーターが使用されます。 有効な値は次のとおりです。  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 どちらのロールを指定しても、アプリケーション、構成、および配置のファイルがインストールされて、SharePoint ファームで PowerPivot for SharePoint を実行できるようになります。 指定したロールに基づいて、SharePoint 統合のハードウェアおよびソフトウェアの要件がチェックされます。  
  
 既存のファーム オプションでは、SharePoint ファームが既に存在することが想定されます。 新しいファーム オプションは、新しいファームでは; を作成することが前提としています。データベース エンジンのインスタンスをファームのデータベース サーバーとして使用できるように、コマンドラインの構文で、データベース エンジンのインスタンスの追加をサポートします。  
  
 以前のリリースとは異なり、すべてのサーバー構成タスクはインストール後のタスクとして実行されます。 インストールと構成の手順を自動化している場合は、PowerShell を使用してサーバーを構成できます。 詳細については、次を参照してください。 [Windows PowerShell を使用して、PowerPivot 構成](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)します。  
  
## <a name="example-commands"></a>コマンドの例  
 次の例では、各オプションの使用方法を示します。 例 1 に示す`SPI_AS_ExistingFarm`します。  
  
```  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 例 2 は `SPI_AS_NewFarm` を示します。 データベース エンジンを準備するパラメーターが含まれています。  
  
```  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="Join"></a> コマンド構文の変更  
 次の手順に従って、コマンド構文の例を変更します。  
  
1.  次のコマンドをコピーして、メモ帳に貼り付けます。  
  
    ```  
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     `/q` パラメーターは、セットアップを非表示モードで実行します。この場合、ユーザー インターフェイスは表示されません。  
  
     `/IAcceptSQLServerLicenseTerms` は、自動インストールのために `/q` パラメーターまたは `/qs` パラメーターを指定する場合に必要です。  
  
     `/action` パラメーターは、インストールを実行するようにセットアップに命令します。  
  
     `/role` パラメーターは、PowerPivot for SharePoint に必要な Analysis Services のプログラム ファイルと構成ファイルをインストールするようにセットアップに命令します。 また、既存のファーム接続情報を検出し、それを使用して SharePoint 構成データベースにアクセスします。 このパラメーターは必須です。 `/features` パラメーターの代わりにこのパラメーターを使用して、インストールするコンポーネントを指定します。  
  
     `/instancename` パラメーターは、名前付きインスタンスとして 'PowerPivot' を指定します。 この値はハードコードされていて変更できません。 ここでは、サービスのインストール方法を示すために指定されています。  
  
     `/indicateprogress` パラメーターは、コマンド プロンプト ウィンドウで進行状況を監視できるようにします。  
  
2.  ここでは、`PID` パラメーターが省略されているため、Evaluation Edition がインストールされます。 Enterprise Edition をインストールする場合は、セットアップ コマンドに PID を追加して、有効なプロダクト キーを指定します。  
  
    ```  
  
    /PID=<product key for an Enterprise installation>  
  
    ```  
  
3.  プレース ホルダー \<domain \username > および\<StrongPassword > を有効なユーザー アカウントとパスワード。  
  
     `/assvaccount`と **/assvcpassword**の構成にパラメーターを使用、[!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]アプリケーション サーバー上のインスタンス。 これらのプレースホルダーを有効なアカウント情報に置き換えます。  
  
     **/Assysadminaccounts**パラメーターは、SQL Server セットアップを実行しているユーザーの id を設定する必要があります。 システム管理者を少なくとも 1 人指定する必要があります。 SQL Server セットアップでは、あらかじめ登録された Administrators グループのメンバーに対して sysadmin 権限が自動的に付与されなくなったことに注意してください。  
  
4.  改行を削除します。  
  
5.  コマンド全体を選択し、クリックして**コピー** [編集] メニュー。  
  
6.  管理者のコマンド プロンプトを開きます。 これを行うには、次のようにクリックします。**開始**をコマンド プロンプトを右クリックし**管理者として実行**します。  
  
7.  SQL Server のインストール メディアを含むドライブまたは共有フォルダーに移動します。  
  
8.  編集済みのコマンドをコマンド ラインに貼り付けます。 これを行うには、コマンド プロンプト ウィンドウの左上隅のアイコンをクリックをポイントして**編集**、 をクリックし、**貼り付け**します。  
  
9. キーを押して**Enter**コマンドを実行します。 セットアップが完了するまで待ちます。 コマンド プロンプト ウィンドウでセットアップの進行状況を監視できます。  
  
10. インストールを確認するには、\Program Files\SQL Server\120\Setup Bootstrap\Log にある summary.txt ファイルを調べます。 サーバーがエラーなしでインストールされていれば、最終結果が "Passed" になっています。  
  
11. サーバーを構成します。 少なくとも、ソリューションを配置し、サービス アプリケーションを作成して、各サイト コレクションで PowerPivot 機能を有効化する必要があります。 詳細については、次を参照してください[構成または修復の PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツール&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)または[サーバーの全体管理で PowerPivot サーバーの管理と構成。](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
## <a name="see-also"></a>参照  
 [PowerPivot サービス アカウントを構成します。](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
