---
title: "Integration Services サーバーで実行中のパッケージの表示と停止 | Microsoft Docs"
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
  - "パッケージ [Integration Services]、管理"
  - "実行中のパッケージの管理 [Integration Services]"
  - "パッケージ [Integration Services]、実行"
  - "実行中のパッケージ [Integration Services]、管理"
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Integration Services サーバーで実行中のパッケージの表示と停止
  **SSISDB** データベースでは、ユーザーに表示されない内部テーブルに実行履歴を格納します。 ただし、必要な情報は、パブリック ビューに対してクエリを実行することで公開されます。 また、パッケージに関連した一般的なタスクを実行するために呼び出すことができるストアド プロシージャも用意されています。  
  
 通常、サーバー上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクトは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で管理します。 また、データベース ビューに対してクエリを実行し、ストアド プロシージャを直接呼び出すことや、マネージ API を呼び出すカスタム コードを記述することもできます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] およびマネージ API では、ビューに対してクエリを実行し、多くのタスクを実行するストアド プロシージャを呼び出します。 たとえば、サーバーで現在実行中の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの一覧を表示し、必要に応じてパッケージの停止を要求できます。  
  
## 実行中のパッケージの一覧の表示  
 **[アクティブな操作]** ダイアログ ボックスでは、サーバーで現在実行中のパッケージの一覧を表示できます。 詳しくは、「 [Active Operations Dialog Box](../../integration-services/performance/active-operations-dialog-box.md)」をご覧ください。  
  
 実行中のパッケージの一覧を表示するその他の方法については、次のトピックをご覧ください。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセス  
 サーバーで実行中のパッケージの一覧を表示するには、ステータスが 2 のパッケージに対してビュー [catalog.executions (SSISDB データベース)](../../integration-services/system-views/catalog-executions-ssisdb-database.md) をクエリします。  
  
 マネージ API を使用したプログラムによるアクセス  
 <xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間とそのクラスを参照してください。  
  
## 実行中のパッケージの停止  
 **[アクティブな操作]** ダイアログ ボックスでは、実行中のパッケージを停止するよう要求できます。 詳しくは、「 [Active Operations Dialog Box](../../integration-services/performance/active-operations-dialog-box.md)」をご覧ください。  
  
 実行中のパッケージを停止するその他の方法については、次のトピックをご覧ください。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセス  
 サーバーで実行中のパッケージを停止するには、ストアド プロシージャ [catalog.stop_operation (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md) を呼び出します。  
  
 マネージ API を使用したプログラムによるアクセス  
 <xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間とそのクラスを参照してください。  
  
## 実行したパッケージの履歴の表示  
 実行したパッケージの履歴を [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で確認するには、 **[すべての実行]** レポートを使用します。 **[すべての実行]** レポートとその他の標準レポートの詳細については、「[Integration Services サーバーのレポート](../../integration-services/performance/reports-for-the-integration-services-server.md)」を参照してください。  
  
 実行中のパッケージの履歴を表示するその他の方法については、次のトピックをご覧ください。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセス  
 実行したパッケージに関する情報を表示するには、ビュー [catalog.executions (SSISDB データベース)](../../integration-services/system-views/catalog-executions-ssisdb-database.md) をクエリします。  
  
 マネージ API を使用したプログラムによるアクセス  
 <xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間とそのクラスを参照してください。  
  
## 参照  
 [プロジェクトとパッケージの実行](https://msdn.microsoft.com/library/hh213290.aspx)   
 [パッケージ実行のレポートのトラブルシューティング](https://msdn.microsoft.com/library/gg471512.aspx)  
  
  