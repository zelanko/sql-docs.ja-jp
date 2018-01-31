---
title: "Integration Services (SSIS) サーバーとカタログ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b1ba94eb985130eb7e3f8ad020756c7387df297c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="integration-services-ssis-server-and-catalog"></a>Integration Services (SSIS) サーバーとカタログ
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でパッケージをデザインしてテストしたら、パッケージを含むプロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーは、**SSISDB** データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスです。 データベースには、パッケージ、プロジェクト、パラメーター、権限、サーバーのプロパティ、および運用履歴というオブジェクトが格納されます。  
  
 **SSISDB** データベース内のオブジェクト情報は、パブリック ビューに対してクエリを実行することで公開されます。 また、データベースには、オブジェクトを管理するために呼び出すことができるストアド プロシージャも用意されています。  
  
 プロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するには、まず **ssDEnoversion** カタログを作成する必要があります。  
  
 SSISDB カタログの機能の概要については、「[SSIS カタログ](../../integration-services/catalog/ssis-catalog.md)」を参照してください。  
  
## <a name="high-availability"></a>高可用性  
 他のユーザー データベースと同様に、 **SSISDB** データベースでデータベース ミラーリングとレプリケーションをサポートします。 ミラーリングとレプリケーションの詳細については、「[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)」を参照してください。  
  
 SSIS と Always On 可用性グループを利用して SSISDB とそのコンテンツの高可用性を実現することもできます。 詳細については、Matt Masson による blogs.msdn.com のブログ記事「[SSIS with Always On](http://go.microsoft.com/fwlink/?LinkId=255873)」 (SSIS と Always On) を参照してください。  
  
##  <a name="ssms"></a> SQL Server Management Studio の Integration Services サーバー  
 **SSISDB** データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続している場合、オブジェクト エクスプローラーに、次のオブジェクトが表示されます。  
  
-   **SSISDB データベース**  
  
     **SSISDB** データベースは、オブジェクト エクスプローラーの **[データベース]** ノードに表示されます。 ビューに対してクエリを実行し、ストアド プロシージャを呼び出して、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーとサーバーに格納されているオブジェクトを管理できます。  
  
-   **統合サービス カタログ**  
  
     **[Integration Services カタログ]** ノードには、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトおよび環境のフォルダーが存在します。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Integration Services サーバー上のパッケージの一覧を表示する](../../integration-services/catalog/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Integration Services (SSIS) プロジェクトとパッケージの配置](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [Integration Services (SSIS) パッケージの実行](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>関連コンテンツ  
 blogs.msdn.com のブログ エントリ「[SSIS with Always On](http://go.microsoft.com/fwlink/?LinkId=255873)」 (SSIS と Always On)。  
  
  
