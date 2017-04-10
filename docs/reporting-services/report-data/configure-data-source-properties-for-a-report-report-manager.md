---
title: "レポートのデータ ソースのプロパティを構成する (レポート マネージャー) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ ソース [Reporting Services], 埋め込み"
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
caps.latest.revision: 44
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 44
---
# レポートのデータ ソースのプロパティを構成する (レポート マネージャー)
  レポートを実行すると、レポート サーバーは、データ ソースへの接続方法を調べるためにプロパティ情報を取得します。 パブリッシュされたレポートの [データ ソース] プロパティ ページには、データ ソースの種類、接続文字列、および資格情報が指定されています。 これらのプロパティを設定することで、データ ソースの接続情報を、レポートの作成時に指定された元の値から変更することができます。  
  
 また、定義済みの共有データ ソースが存在し、そこで使用する接続情報が既に指定されている場合は、代わりにその共有データ ソースを指定することもできます。 共有データ ソースを使用するには、レポートの [データ ソース] プロパティ ページの **[共有データ ソース]** をクリックします。  
  
### 埋め込みデータ ソースを構成するには  
  
1.  [レポート マネージャー (SSRS ネイティブ モード)](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md) を開始します。  
  
2.  レポート マネージャーで **[コンテンツ]** ページに移動します。 レポート固有のデータ ソースを構成するレポートに移動し、そのレポートを開きます。  
  
3.  **[プロパティ]** タブをクリックします。 **[全般]** プロパティ ページが開きます。  
  
4.  **[データ ソース]** タブをクリックします。 レポートの [データ ソース] プロパティ ページが開きます。  
  
5.  **[カスタム データ ソース]** をクリックして、レポート内のデータ ソース接続情報を指定します。  
  
6.  **[接続の種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を指定します。  
  
7.  **[接続文字列]**でレポート サーバーがデータ ソースへの接続に使用する接続文字列を指定します。 接続文字列には資格情報を指定しないことをお勧めします。  
  
     以下に、ローカルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースへの接続に使用する接続文字列の例を示します。  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  **[接続に使用する認証]**では、レポートが実行される際に資格情報を取得する方法を指定します。  
  
    -   ユーザーにログオン名とパスワードを要求する場合は、 **[レポートの実行者により指定された資格情報]**をクリックします。  
  
    -   サブスクリプションやその他のスケジュールに設定された操作 (自動レポート履歴生成など) をサポートするレポートでデータ ソースを使用する場合は、**[レポート サーバーに保存され、セキュリティで保護された資格情報]** をクリックします。  
  
    -   レポート サーバーが、レポートにアクセスするユーザーの資格情報を、外部データ ソースをホストするサーバーに渡す場合は、 **[Windows 統合セキュリティ]**をクリックします。 この場合、ユーザーはユーザー名やパスワードを入力することを要求されません。  
  
    -   データ ソースで資格情報を使用しない場合 (ファイル システムからアクセス可能な XML ファイルをデータ ソースとして使用する場合など) は、**[資格情報は必要ありません]** をクリックします。 この資格情報オプションは、使用するデータ ソースで妥当と考えられる場合にのみ指定してください。 認証を必要とするデータ ソースに対してこのオプションを選択した場合、接続エラーが発生します。 このオプションを選択する場合は、ユーザーの資格情報を利用できない場合に、レポート サーバーが他のコンピューターに接続して、データまたはファイルを取得できるように、必ず自動実行アカウントを構成してください。  
  
 資格情報の構成の詳細については、「[レポート データ ソースに関する資格情報と接続情報を指定する](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)」を参照してください。 自動実行アカウントの詳細については、「[自動実行アカウントの構成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。  
  
## 参照  
 [[コンテンツ] ページ (レポート マネージャー)](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [[新しいデータ ソース] ページ (レポート マネージャー)](../Topic/New%20Data%20Source%20Page%20\(Report%20Manager\).md)   
 [共有データ ソースを作成、変更、および削除する (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [レポート データ ソースを管理する](../../reporting-services/report-data/manage-report-data-sources.md)   
 [共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [[データ ソース] プロパティ ページ (レポート マネージャー)](../Topic/Data%20Sources%20Properties%20Page%20\(Report%20Manager\).md)  
  
  