---
title: "SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージの表示"
  - "接続 [Integration Services], パッケージ"
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス)
    
> [!IMPORTANT]  
>  このトピックでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、以前のリリースの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
 この手順では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に接続して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが管理するパッケージの一覧を表示する方法について説明します。  
  
### Integration Services に接続するには  
  
1.  **[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[Microsoft SQL Server]** の順にポイントし、**[SQL Server Management Studio]** をクリックします。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスで、**[サーバーの種類]** 一覧の **[Integration Services]** を選択し、**[サーバー名]** ボックスにサーバー名を入力して **[接続]** をクリックします。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に接続できない場合は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが実行されていない可能性があります。 このサービスのステータスを調べるには、**[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[Microsoft SQL Server]**、**[構成ツール]** の順にポイントして、**[SQL Server 構成マネージャー]** をクリックします。 左ペインで、 **[SQL Server のサービス]**をクリックします。 右ペインで、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスを見つけます。 サービスがまだ実行されていない場合は開始します。  
  
     [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] が開きます。 既定では、Management Studio の左下隅にオブジェクト エクスプローラーが開きます。 オブジェクト エクスプローラーが開いていない場合は、**[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。  
  
### Integration Services サービスが管理するパッケージを表示するには  
  
1.  オブジェクト エクスプローラーで、[格納されたパッケージ] フォルダーを展開します。  
  
2.  [格納されたパッケージ] サブフォルダーを展開して、パッケージを表示します。  
  
## 参照  
 [パッケージの管理 (SSIS サービス)](../../integration-services/service/package-management-ssis-service.md)   
 [SQL Server Management Studio の使用 [SQL Server]](../../ssms/use-sql-server-management-studio.md)  
  
  