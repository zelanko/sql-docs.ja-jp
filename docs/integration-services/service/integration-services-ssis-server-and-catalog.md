---
title: "Integration Services (SSIS) サーバーとカタログ | Microsoft Docs"
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
  - "パッケージ [Integration Services]、管理"
  - "パッケージの管理 [Integration Services]"
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Integration Services (SSIS) サーバーとカタログ
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でパッケージをデザインしてテストしたら、パッケージを含むプロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置できます。  
  
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Server のインスタンスである、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] をホストする、 **SSISDB** データベースです。 データベースには、パッケージ、プロジェクト、パラメーター、権限、サーバーのプロパティ、および運用履歴というオブジェクトが格納されます。  
  
 **SSISDB** データベース内のオブジェクト情報は、パブリック ビューに対してクエリを実行することで公開されます。 また、データベースには、オブジェクトを管理するために呼び出すことができるストアド プロシージャも用意されています。  
  
 プロジェクトを展開する前に、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーを作成する必要がある、 **SSISDB** カタログです。  
  
 SSISDB カタログの機能の概要については、次を参照してください。 [SSIS カタログ](../../integration-services/service/ssis-catalog.md)します。  
  
## 高可用性  
 他のユーザー データベースと同様に、 **SSISDB** データベースでデータベース ミラーリングとレプリケーションをサポートします。 ミラーリングとレプリケーションの詳細については、次を参照してください。 [データベース ミラーリングと #40 です。SQL Server と #41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)します。  
  
 ことによって、SSISDB とそのコンテンツの高可用性を提供することも SSIS と Alwayson 可用性グループを使用します。 詳細については、ブログ、Matt Masson による投稿を参照してください。 [では常にの SSIS](http://go.microsoft.com/fwlink/?LinkId=255873), 、blogs.msdn.com です。  
  
##  <a name="ssms"></a> SQL Server Management Studio の Integration Services サーバー  
 インスタンスに接続する場合、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] をホストする、 **SSISDB** データベース、オブジェクト エクスプ ローラーで、次のオブジェクトを参照してください。  
  
-   **SSISDB データベース**  
  
     **SSISDB** データベースは、オブジェクト エクスプローラーの **[データベース]** ノードに表示されます。 ビューに対してクエリを実行し、ストアド プロシージャを呼び出して、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーとサーバーに格納されているオブジェクトを管理できます。  
  
-   **統合サービス カタログ**  
  
     **[Integration Services カタログ]** ノードには、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトおよび環境のフォルダーが存在します。  
  
## 関連タスク  
  
-   [SSIS カタログの作成](../../integration-services/service/create-the-ssis-catalog.md)  
  
-   [Integration Services サーバー上のパッケージの一覧を表示する](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Integration Services サーバーへのプロジェクトの配置](../../integration-services/packages/deploy-projects-to-integration-services-server.md)  
  
-   [SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## 関連コンテンツ  
 ブログ エントリ「 [で常にの SSIS](http://go.microsoft.com/fwlink/?LinkId=255873), 、blogs.msdn.com です。  
  
  