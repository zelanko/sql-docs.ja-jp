---
title: "パッケージの管理 (SSIS サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Integration Services パッケージ, 管理"
  - "パッケージ [Integration Services]、管理"
  - "Integration Services パッケージ、管理"
  - "パッケージの格納"
  - "[格納されたパッケージ] フォルダー"
  - "現在のパッケージ"
  - "[実行中のパッケージ] フォルダー"
  - "状態情報 [Integration Services]"
  - "SSIS パッケージ, 管理"
  - "ストレージ [Integration Services]"
  - "監視 [Integration Services], パッケージ"
  - "Integration Services サービス, パッケージの管理"
  - "サービス [Integration Services], パッケージの管理"
ms.assetid: 0261ed9e-3b01-4e37-a9d4-d039c41029b6
caps.latest.revision: 59
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 57
---
# パッケージの管理 (SSIS サービス)
  パッケージの管理には、次のタスクを含むいくつかのタスクを伴います。  
  
-   実行中のパッケージの監視  
  
-   パッケージ ストレージの管理  
  
-   パッケージのインポートおよびエクスポート  
  
> [!IMPORTANT]  
>  このトピックでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  では、以前のリリースの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
## パッケージ ストア  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  には、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージにアクセスするための 2 つの最上位フォルダーである **[実行中のパッケージ]** と **[格納されたパッケージ]** があります。 **[実行中のパッケージ]** フォルダーには、サーバーで現在実行中のパッケージが一覧表示されます。 **[格納されたパッケージ]** フォルダーには、パッケージ ストアに保存されたパッケージが一覧表示されます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが管理するパッケージは、これらのパッケージのみです。 パッケージ ストアは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスの構成ファイルで一覧されている msdb データベースとファイル システム フォルダーのいずれかまたは両方で構成することができます。 この構成ファイルは、管理する msdb とファイル システム フォルダーを指定します。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが管理していないパッケージは、ファイル システム内の他の場所に保存することもできます。  
  
 msdb に保存するパッケージは、sysssispackages というテーブルに格納されます。 パッケージを msdb に保存するとき、論理フォルダーに格納してグループ化できます。 論理フォルダーを使用することで、パッケージを目的別に整理したり、sysssispackages テーブルでパッケージをフィルター処理したりできます。 新しい論理フォルダーを作成するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用します。 既定では、msdb に追加する論理フォルダーは自動的にパッケージ ストアに含まれます。  
  
 msdb 内のパッケージをグループ化するために作成する論理フォルダーは、msdb 内の sysssispackagefolders テーブルの行として表現されます。 sysssispackagefolders の folderid 列と parentfolderid 列は、フォルダー階層を定義します。 msdb のルート論理フォルダーは、parentfolderid 列が NULL 値である sysssispackagefolders の行です。 詳細については、「[sysssispackages (Transact-SQL)](../../relational-databases/system-tables/sysssispackages-transact-sql.md)」および「[sysssispackagefolders (Transact-SQL)](../../relational-databases/system-tables/sysssispackagefolders-transact-sql.md)」を参照してください。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開いて [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に接続すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが管理する msdb フォルダーが、[格納されたパッケージ] フォルダー内に一覧表示されます。 構成ファイルでルート ファイル システム フォルダーを指定している場合は、[格納されたパッケージ] フォルダーにファイル システムのルート フォルダーとすべてのサブフォルダーに保存されているパッケージも一覧表示されます。  
  
 パッケージは任意のファイル システム フォルダーに保存できますが、そのフォルダーをパッケージ ストアの構成ファイルのフォルダー一覧に追加していない場合、**[格納されたパッケージ]** フォルダーのサブフォルダーにはパッケージが一覧表示されません。 構成ファイルの詳細については、「[Integration Services サービスの構成 (SSIS サービス)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)」を参照してください。  
  
 **[実行中のパッケージ]** フォルダーにはサブフォルダーがなく、拡張もできません。  
  
 既定では、**[格納されたパッケージ]** フォルダーには、**[ファイル システム]** と **[MSDB]** の 2 つのフォルダーがあります。 **[ファイル システム]** フォルダーには、ファイル システムに保存されるパッケージが一覧表示されます。 これらのファイルの場所は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスの構成ファイルで指定されます。 既定のフォルダーは、%Program Files%\Microsoft SQL Server\100\DTS の Packages フォルダーです。 **[MSDB]** フォルダーには、サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb データベースに保存されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージが一覧表示されます。 sysssispackages テーブルには、msdb に保存されるパッケージが格納されています。  
  
 パッケージ ストア内のパッケージの一覧を表示するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に接続する必要があります。 詳細については、「[SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス)](../../integration-services/service/view-integration-services-packages-in-sql-server-management-studio-ssis-service.md)」を参照してください。  
  
## 実行中のパッケージの監視  
 **[実行中のパッケージ]** フォルダーには、現在実行中のパッケージが一覧表示されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[概要]** ページに現在のパッケージ情報を表示するには、**[実行中のパッケージ]** フォルダーをクリックします。 実行中のパッケージの実行時間などの情報が **[概要]** ページに一覧表示されます。 必要に応じて、フォルダーを更新して、最新の情報を表示します。  
  
 実行中の単一のパッケージに関する情報を **[概要]** ページに表示するには、該当するパッケージをクリックします。 **[概要]** ページには、パッケージのバージョンや説明などの情報が表示されます。  
  
 **[実行中のパッケージ]** フォルダーで実行中のパッケージを右クリックしてから、**[停止]** をクリックすると、実行中のパッケージを停止できます。  
  
## パッケージ ストレージの管理  
 パッケージを整理するために、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスによって構成ファイルに一覧表示されるルート パッケージ ストア フォルダーにカスタム フォルダーを追加できます。 既定では、ルート フォルダーは **[ファイル システム]** フォルダーと **[MSDB]** フォルダーです。 たとえば、**[ファイル システム]** フォルダーに、データ クリーンに使用するすべてのパッケージを格納する **[データ クリーン]** フォルダーを追加できます。 カスタム フォルダー内にカスタム フォルダーを追加して、必要に合わせて入れ子にしたフォルダー階層を作成できます。 カスタム フォルダーは削除や名前の変更が可能ですが、構成ファイルで指定されているルート フォルダーの名前の変更や削除はできません。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で一覧表示されるルート フォルダーを更新するには、構成ファイルを更新する必要があります。  
  
 詳細については、「[Integration Services サービスの構成 (SSIS サービス)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)」を参照してください。  
  
## パッケージのインポートおよびエクスポート  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  パッケージは、msdb データベースまたはファイル システムに保存できます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインポートまたはエクスポート機能を使用して、一方のストレージ型から別のストレージ型にパッケージをコピーできます。 また、同じストレージ型にパッケージをインポートして別の名前を付け、パッケージのコピーを作成することもできます。 パッケージのインポートおよびエクスポートには、**dtutil** コマンド プロンプト ユーティリティ (dtutil.exe) も使用できます。  
  
 詳細については、「[dtutil ユーティリティ](../../integration-services/dtutil-utility.md)」を参照してください。  
  
## 関連タスク  
  
-   [パッケージをインポートおよびエクスポートする (SSIS サービス)](../../integration-services/service/import-and-export-packages-ssis-service.md)  
  
-   [SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス)](../../integration-services/service/view-integration-services-packages-in-sql-server-management-studio-ssis-service.md)  
  
## 参照  
 [Integration Services サービス (SSIS サービス)](../../integration-services/service/integration-services-service-ssis-service.md)  
  
  