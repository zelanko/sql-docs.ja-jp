---
title: "SQL Server R サービスの無人インストール | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 14
---
# SQL Server R サービスの無人インストール
    
インストール プロセスを開始する前に、これらの要件を確認してください。

+ R サービス (データベース) を使用する各インスタンスにデータベース エンジンをインストールする必要があります [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。  
+ オフライン インストールを実行する場合は、R の必須コンポーネントを事前にダウンロードおよびローカル フォルダーにコピーする必要があります。 ダウンロードの場所を参照してください。 [インターネットのアクセス権のない R コンポーネントのインストール中](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)します。   
+ 新しいパラメーターがある */IACCEPTROPENLICENSETERMS*, 、オープン ソース R のコンポーネントを使用するためのライセンス条項を承諾していることを示します。 コマンドラインでこのパラメーターが含まれない場合は、セットアップは失敗します。  
  
## R サービス (In-Database) の無人インストールの実行  
 次の例は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
###  <a name="bkmk_Unattended"></a>  
  
1.  コマンド プロンプトから次のコマンドを実行します。  
  
    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,AdvancedAnalytics /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS  
    ```  
  
2.  インストールが完了したら、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で次のコマンドを実行して機能を有効にします。  
  
    ```  
    Exec sp_configure  'external scripts enabled', 1  
    Reconfigure  with  override  
  
    ```  
  
    > [!NOTE]  
    >  エンジンの機能を明示的に有効にする必要があります。そうしないと、セットアップによって機能がインストールおよび構成されている場合でも、機能は R スクリプトを呼び出すことができません。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再起動します。 関連する [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスも自動的に再起動されます。  
  
## 参照  
 [R Services のセットアップのトラブルシューティング](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  