---
title: "登録済みのフィルターおよびワード ブレーカーの表示または変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フルテキスト検索 [SQL Server], ワード ブレーカー"
  - "フルテキスト検索 [SQL Server], フィルター"
  - "フィルター [フルテキスト検索]"
  - "ワード ブレーカー [フルテキスト検索]"
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# 登録済みのフィルターおよびワード ブレーカーの表示または変更
  システム上で任意のワード ブレーカーまたはフィルターのインストールまたはアンインストールを行った後、その変更はサーバー インスタンスに自動的に反映されません。 このトピックでは、現在登録されているワード ブレーカーまたはフィルターを表示する方法と、新しくインストールされたワード ブレーカーおよびフィルターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに登録する方法について説明します。  
  
### ワード ブレーカーが現在登録されている言語の一覧を表示するには  
  
1.  [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) カタログ ビューを使用します。次に例を示します。  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### 現在登録されているフィルターの一覧を表示するには  
  
1.  [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) システム ストアド プロシージャを使用します。次に例を示します。  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### 新しくインストールされたワード ブレーカーおよびフィルターを登録するには  
  
1.  [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md) システム ストアド プロシージャを使用して、言語の一覧を更新します。次に例を示します。  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### アンインストールされたワード ブレーカーおよびフィルターを登録解除するには  
  
1.  **sp_fulltext_service** を使用して、言語の一覧を更新します。次に例を示します。  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  **sp_fulltext_service** を使用して、フィルター デーモン ホスト プロセス (fdhost.exe) を起動します。次に例を示します。  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### 新しいワード ブレーカーまたはフィルターのインストール時に既存のワード ブレーカーまたはフィルターを置き換えるには  
  
1.  新しいワード ブレーカーまたはフィルターを含む DLL ファイルのインストールを準備するときに、そのファイル名サーバー インスタンスにインストールされている既存の DLL ファイルとは異なることを確認します。  
  
2.  サーバー インスタンスの標準 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL ファイルが格納されているディレクトリに新しい DLL ファイルをコピーします。 既定の場所は次のとおりです。  
  
     C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn  
  
    > [!IMPORTANT]  
    >  署名付きの検証されたコンポーネントのみを読み込むようにすることを強くお勧めします。 さらに、FDHOST ランチャー (MSSQLFDLauncher) サービスは、必要最小限の特権で実行することをお勧めします。  
  
3.  新しいワード ブレーカーまたはフィルターをインストールします。  
  
     **Microsoft Filter Pack IFilters をインストールして読み込むには**  
  
    -   [How to register Microsoft Filter Pack IFilters with SQL Server (Microsoft Filter Pack の IFilter を SQL Server に登録する方法)](http://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  **sp_fulltext_service** を使用して、新しくインストールされたワード ブレーカーおよびフィルターをサーバー インスタンスに読み込みます。次に例を示します。  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  **sp_fulltext_service** を使用して、言語の一覧を更新します。次に例を示します。  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  **sp_fulltext_service** を使用して、フィルター デーモン ホスト プロセス (fdhost.exe) を再起動します。次に例を示します。  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## 参照  
 [フルテキスト フィルター デーモン ランチャーのサービス アカウントの設定](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [検索用フィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  