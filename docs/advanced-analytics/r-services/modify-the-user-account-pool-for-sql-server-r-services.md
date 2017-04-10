---
title: "SQL Server R サービスのユーザー アカウント プールを変更する | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# SQL Server R サービスのユーザー アカウント プールを変更する
  インストール プロセスの一部として [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、新しい Windows *ユーザー アカウントのプール* ごとのタスクの実行をサポートするために作成された、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスです。 これらの作業者のアカウントの目的は、別の SQL ユーザーが R スクリプトの同時実行を分離します。
  
  このプールのユーザー アカウント数によって、同時にアクティブにすることができる R セッション数が決まります。   同じユーザーが同時に複数の R スクリプトを実行、セッションがそのユーザーが実行すべてと同じワーカー アカウントが使用します。 その結果、1 人のユーザーには、100 の異なる R スクリプトを同時に限り実行リソースを許可があります。

## 既定の構成   
-   既定のインスタンスでは、グループ名 **SQLRUserGroup**します。 
-   インスタンス名を持つ名前付きインスタンスの既定のグループ名が付加されたもの。 たとえば、 **SQLRUserGroupMyInstanceName**します。 
-   アカウント: 既定では、ユーザー アカウントのプール 20 ユーザー アカウントを含む、名前付き **MSSQLSERVER01** を通じて **MSSQLSERVER20** の既定のインスタンス。  
-   インスタンス名を使用して名前付きインスタンスからユーザー アカウントに名前が: たとえば、 **MyInstanceName01** を通じて **MyInstanceName20**します。  


## 各インスタンスのユーザー グループを管理します。
Windows アカウント グループを作成者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] R サービスがインストールされている、R をサポートする複数のインスタンスをインストールしている場合があるため複数のユーザー グループ インスタンスごとにセットアップします。
ただし、各ユーザー グループに関連付けられている、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] 特定のインスタンスのサービスし、他のインスタンス上で実行される R のジョブをサポートすることはできません。

グループには既定では、 **いない** に対するログイン権限がある、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が関連付けられているインスタンス。 データベース管理者はこのグループに、ユーザーが R スクリプトの実行を有効にするに場合 **への接続** アクセス許可。  

### Windows ユーザー グループ内のワーカー アカウント数を変更します。

アカウントのプール内のユーザーの数を変更するには、プロパティを編集する必要があります、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] 以下に示すようにサービスを提供します。  
  
各ユーザー アカウントに関連付けられているパスワードがランダムに生成されたが変更できますに後で、アカウントが作成されるとします。  
  
1. SQL Server 構成マネージャーを開き、選択 **SQL Server サービス**します。
2. SQL Server スタート パッド サービスをダブルクリックし、サービスが実行されている場合は停止します。 
3.   **サービス** ] タブで、[開始モードが [自動] に設定されていることを確認します。 スタート パッドが実行されていない場合、R スクリプトは失敗します。
4.  をクリックして、 **詳細** タブおよびの値を編集 **外部のユーザー数** 必要な場合です。 この設定は、さまざまな SQL ユーザーの数が R. でクエリを同時に実行できるを制御します。既定ではアカウントは 20 個、ほとんどの場合は R セッションをサポートするために十分であります。
5. オプションを設定する必要に応じて、 **外部ユーザーのパスワードをリセット** に _はい_ 組織にパスワードを 90 日ごとに変更を必要とするポリシーがある場合。 これを行うと、スタート パッドは、ユーザー アカウントに対して保持している暗号化されたパスワードを再生成されます。    
6.  サービスを再起動します。  

## リモート スクリプト実行に必要な追加のアクセス許可
実行する場合にリモートとして SQL Server コンピューターに R スクリプトのコンテキストを計算する、このワーカーのグループには、R スクリプトを実行する SQL Server インスタンスにログインする権限が必要があります。

詳細については、次を参照してください。 [アップグレードとインストールに関する FAQ](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)します。 

  
## 参照  
 [構成 (SQL Server R Services)](../../advanced-analytics/r-services/configuration-sql-server-r-services.md)
  