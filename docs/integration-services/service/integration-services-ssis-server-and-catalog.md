---
title: "Integration Services (SSIS) サーバーとカタログ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 939f31adf1ab0a975bd4339dabab310ef9025049
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-server-and-catalog"></a>Integration Services (SSIS) サーバーとカタログ
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でパッケージをデザインしてテストしたら、パッケージを含むプロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Server のインスタンスである、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]をホストする、 **SSISDB**データベース。 データベースには、パッケージ、プロジェクト、パラメーター、権限、サーバーのプロパティ、および運用履歴というオブジェクトが格納されます。  
  
 **SSISDB** データベース内のオブジェクト情報は、パブリック ビューに対してクエリを実行することで公開されます。 また、データベースには、オブジェクトを管理するために呼び出すことができるストアド プロシージャも用意されています。  
  
 プロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するには、まず **ssDEnoversion** カタログを作成する必要があります。  
  
 SSISDB カタログの機能の概要については、次を参照してください。 [SSIS カタログ](../../integration-services/service/ssis-catalog.md)です。  
  
## <a name="high-availability"></a>高可用性  
 他のユーザー データベースと同様に、 **SSISDB** データベースでデータベース ミラーリングとレプリケーションをサポートします。 ミラーリングとレプリケーションの詳細については、次を参照してください。[データベース ミラーリング & #40 です。SQL Server &#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 ことで、SSISDB とその内容の高可用性を提供することも SSIS と Always On 可用性グループを使用します。 詳細については、このによるブログ投稿「Matt Masson、を参照してください。 [SSIS と Always On](http://go.microsoft.com/fwlink/?LinkId=255873)blogs.msdn.com のです。  
  
##  <a name="ssms"></a> SQL Server Management Studio の Integration Services サーバー  
 インスタンスに接続する場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]をホストする、 **SSISDB**データベース、オブジェクト エクスプ ローラーで、次のオブジェクトを参照してください。  
  
-   **SSISDB データベース**  
  
     **SSISDB** データベースは、オブジェクト エクスプローラーの **[データベース]** ノードに表示されます。 ビューに対してクエリを実行し、ストアド プロシージャを呼び出して、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーとサーバーに格納されているオブジェクトを管理できます。  
  
-   **統合サービス カタログ**  
  
     **[Integration Services カタログ]** ノードには、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトおよび環境のフォルダーが存在します。  
  
## <a name="related-tasks"></a>関連タスク  
  
-   [Integration Services サーバーでパッケージの一覧を表示します。](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Integration Services (SSIS) の展開のプロジェクトとパッケージ](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [Integration Services (SSIS) パッケージの実行](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>関連コンテンツ  
 ブログ エントリ「 [SSIS と Always On](http://go.microsoft.com/fwlink/?LinkId=255873)blogs.msdn.com のです。  
  
  

