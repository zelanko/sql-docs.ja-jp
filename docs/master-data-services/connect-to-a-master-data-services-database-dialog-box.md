---
title: "[マスター データ サービス データベースへの接続] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.mds.configmanager.srvconnect.f1"
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# [マスター データ サービス データベースへの接続] ダイアログ ボックス
  **[マスター データ サービス データベースへの接続]** ダイアログ ボックスを使用して、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択します。  
  
 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]では、このダイアログは次のページから利用できます。  
  
-   **[データベース構成]** ページで **[データベースの選択]** をクリックします。 このダイアログを使用して、システム設定を構成するデータベースを選択します。  
  
-   **[Web の構成]** ページで **[アプリケーションとデータベースの関連付け]** の **[選択]** をクリックし、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サイトまたはアプリケーションと関連付けるデータベースを選択します。  
  
## [データベースの選択]  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースをホストするローカルまたはリモートの [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] インスタンスに接続するための情報を指定します。 リモート インスタンスに接続するには、そのインスタンスでリモート接続を有効にする必要があります。  
  
|コントロール名|Description|  
|------------------|-----------------|  
|**SQL Server インスタンス (SQL Server instance)**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースをホストするために必要な [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] インスタンス名を指定します。 ここには、ローカルまたはリモートのコンピューターの、既定または名前付きのインスタンスを指定できます。 次のように入力して、情報を指定します。<br /><br /> ローカル コンピューター上の既定のインスタンスに接続するには、ピリオド (.) を入力します。<br /><br /> 指定したローカル コンピューターまたはリモート コンピューター上の既定のインスタンスに接続するには、サーバー名または IP アドレスを入力します。<br /><br /> 指定したローカル コンピューターまたはリモート コンピューター上の名前付きインスタンスに接続するには、サーバー名または IP アドレスと、インスタンス名を入力します。 この情報は、*server_name*\\*instance_name* の形式で指定します。|  
|**認証の種類**|指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスへの接続時に使用する認証の種類を選択します。 接続に使用する資格情報によって、**[マスター データ サービス データベース]** ドロップダウン リストに表示されるデータベースが決まります。<br /><br /> 認証の種類は次のとおりです。<br /><br /> **[現在のユーザー – 統合セキュリティ]**: 現在の Windows ユーザー アカウントの資格情報を使用して接続するときに、統合 Windows 認証を使用します。 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] では、コンピューターにログオンしてアプリケーションを開いたユーザーの Windows 資格情報が使用されます。 アプリケーションで別の Windows 資格情報を指定することはできません。 別の Windows 資格情報を使用して接続する場合は、そのユーザーとしてコンピューターにログオンし、[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]を開く必要があります。<br /><br /> **[SQL Server アカウント]**: 接続する際に SQL Server アカウントを使用します。 このオプションを選択すると、**[ユーザー名]** フィールドと **[パスワード]** フィールドが有効になり、指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] アカウントの資格情報を指定する必要があります。|  
|**ユーザー名**|指定した SQL Server インスタンスへの接続に使用されるユーザー アカウントの名前を指定します。 アカウントは、指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの **sysadmin** ロールに属している必要があります。<br /><br /> **[認証の種類]** が **[現在のユーザー - 統合セキュリティ]** の場合、**[ユーザー名]** ボックスは読み取り専用で、コンピューターにログオンした Windows ユーザー アカウント名が表示されます。<br /><br /> **[認証の種類]** が **[SQL Server アカウント]** の場合、**[ユーザー名]** ボックスが有効になり、指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] アカウントの資格情報を指定する必要があります。|  
|**Password**|ユーザー アカウントに関連付けられているパスワードを指定します。<br /><br /> **[認証の種類]** が **[現在のユーザー - 統合セキュリティ]** の場合、**[パスワード]** ボックスは読み取り専用で、指定した Windows ユーザー アカウントの資格情報が接続に使用されます。<br /><br /> **[認証の種類]** が **[SQL Server アカウント]** の場合、**[パスワード]** ボックスが有効になり、指定したユーザー アカウントに関連付けられているパスワードを指定する必要があります。|  
|**Connect**|指定した資格情報を使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続します。|  
|**[Master Data Services データベース]**|次の基準に基づいて、指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス内の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースが表示されます。<br /><br /> ユーザーがそのインスタンスの **sysadmin** サーバー ロールのメンバーである場合は、そのインスタンス内の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースがすべて表示されます。<br /><br /> ユーザーがそのインスタンスに含まれるいずれかの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの **db_owner** データベース ロールのメンバーである場合は、それらの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースが表示されます。<br /><br/> SQL Server ロールの詳細については、「[サーバー レベルのロール](../relational-databases/security/authentication-access/server-level-roles.md)」および「[データベース レベルのロール](../relational-databases/security/authentication-access/database-level-roles.md)」を参照してください。|  
  
## 参照  
 [[データベース構成] ページ (マスター データ サービス構成マネージャー)](../Topic/Database%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)   
 [マスター データ サービスの概要 (SQL Server 2016)](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)  
  
  