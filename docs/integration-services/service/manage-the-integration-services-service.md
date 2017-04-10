---
title: "Integration Services サービスを管理する | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integration Services サービス, 構成"
  - "サービス [Integration Services], 構成"
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 63
---
# Integration Services サービスを管理する
    
> **重要!!** このトピックでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、以前のリリースの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントのインストール時に、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスもインストールされます。 既定では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが起動され、スタートアップの種類が自動に設定されます。 ただし、サービスを使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の格納されたパッケージおよび実行中のパッケージを管理するには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] をインストールする必要があります。  
  
> **注:** レガシー Integration Services サービスに直接接続するには、Integration Services サービスが実行されている SQL Server のバージョンと合わせたバージョンの SQL Server Management Studio (SSMS) を使用する必要があります。 たとえば、SQL Server 2016 のインスタンスで実行されているレガシー Integration Services サービスに接続するには、SQL Server 2016 用にリリースされたバージョンの SSMS を使用する必要があります。 [SQL Server Management Studio (SSMS) をダウンロードします](https://msdn.microsoft.com/library/mt238290.aspx)。
>
>   SSMS の **[サーバーへの接続]** ダイアログ ボックスで、旧バージョンの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが実行されているサーバーの名前を入力することはできません。 ただし、リモート サーバーに格納されるパッケージを管理するために、そのリモート サーバー上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスのインスタンスに接続する必要はありません。 代わりに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスの構成ファイルを編集し、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でリモート サーバーに格納されているパッケージが表示されるようにします。 詳細については、「[Integration Services サービスの構成 (SSIS サービス)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)」を参照してください。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスのインスタンスは 1 台のコンピューターに 1 つだけインストールできます。 このサービスは、[!INCLUDE[ssDE](../../includes/ssde-md.md)] の特定のインスタンスに固有ではありません。 サービスに接続するには、サービスが実行されているコンピューターの名前を使用します。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、SQL Server 構成マネージャーまたはサービスのいずれかの Microsoft 管理コンソール (MMC) スナップインを使用して管理できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でパッケージを管理するには、事前にサービスを起動しておく必要があります。  
  
 既定では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、[!INCLUDE[ssDE](../../includes/ssde-md.md)] と同時にインストールされる[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のインスタンスの msdb データベース内にあるパッケージを管理するように構成されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが同時にインストールされない場合、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のローカルの既定インスタンスの msdb データベース内にあるパッケージを管理するように構成されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の名前付きインスタンスまたはリモート インスタンス、あるいは [!INCLUDE[ssDE](../../includes/ssde-md.md)] の複数のインスタンスに格納されているパッケージを管理するには、サービスの構成ファイルを変更する必要があります。 詳細については、「[Integration Services サービスの構成 (SSIS サービス)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)」を参照してください。  
  
 既定では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが停止すると、パッケージの実行も停止するように設定されています。 ただし、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスはパッケージが停止するまで待機しないため、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスの停止後に実行を続けるパッケージもあります。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが停止した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザード、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナー、パッケージ実行ユーティリティ、および **dtexec** コマンド プロンプト ユーティリティ (dtexec.exe) を使用してパッケージを実行し続けることができます。 ただし、実行中のパッケージを監視することはできません。  
  
 既定では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは NETWORK SERVICE アカウントのコンテキスト内で実行されます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは Windows のイベント ログに書き込みを行います。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサービス イベントを表示できます。 Windows イベント ビューアーを使用してサービス イベントを表示することもできます。  
  
### サービス スナップインを使用して Integration Services サービスのプロパティを設定するには  
  
-   [Integration Services サービスのプロパティを設定する](../../integration-services/service/set-the-properties-of-the-integration-services-service.md)  
  
### Integration Services のサービス イベントを表示するには  
  
-   [Integration Services サービスのイベントを表示する](../../integration-services/service/view-events-for-the-integration-services-service.md)  
  
## 参照  
 [Integration Services サービス (SSIS サービス)](../../integration-services/service/integration-services-service-ssis-service.md)   
 [Integration Services サービスの構成 (SSIS サービス)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)   
 [SQL Server インポートおよびエクスポート ウィザード](../Topic/SQL%20Server%20Import%20and%20Export%20Wizard.md)   
 [dtexec ユーティリティ](../../integration-services/packages/dtexec-utility.md)   
 [プロジェクトとパッケージの実行](https://msdn.microsoft.com/library/ms141708(v=sql.130).aspx)  
  
  