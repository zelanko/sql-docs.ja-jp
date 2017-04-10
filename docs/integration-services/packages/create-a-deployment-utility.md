---
title: "配置ユーティリティを作成する | Microsoft Docs"
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
  - "パッケージの配置 [Integration Services], 配置ユーティリティ"
  - "配置ユーティリティ [Integration Services]"
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# 配置ユーティリティを作成する
  パッケージ配置の最初の手順は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトの配置ユーティリティを作成することです。 配置ユーティリティは、別のサーバーに [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトのパッケージを配置する際に必要となるファイルを格納したフォルダーです。 配置ユーティリティは [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトが格納されているコンピューター上に作成されます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトのパッケージ配置ユーティリティを作成するには、最初に配置ユーティリティ作成用のビルド プロセスを設定してから、プロジェクトをビルドします。 プロジェクトをビルドすると、プロジェクトのすべてのパッケージおよびパッケージの構成が自動的に追加されます。 Readme ファイルなどのファイルをプロジェクトに追加して配置するには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトの **[その他]** フォルダーにファイルを格納します。 プロジェクトのビルド時に、これらのファイルも自動的に追加されます。  
  
 プロジェクト配置は個別に設定できます。 プロジェクトをビルドしてパッケージ配置ユーティリティを作成する前に、配置ユーティリティのプロパティを設定して、プロジェクトのパッケージの配置方法をカスタマイズできます。 たとえば、プロジェクトの配置時にパッケージの構成を更新するかどうかを指定できます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトのプロパティにアクセスするには、プロジェクトを右クリックして **[プロパティ]** をクリックします。  
  
 次の表に、配置ユーティリティのプロパティの一覧を示します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|AllowConfigurationChange|配置の際に構成を更新するかどうかを指定する値。|  
|CreateDeploymentUtility|プロジェクトのビルド時にパッケージ配置ユーティリティを作成するかどうかを指定する値。 配置ユーティリティを作成するには、このプロパティが **True** である必要があります。|  
|DeploymentOutputPath|配置ユーティリティの場所。[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトから見た相対的な位置。|  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトをビルドすると、\<プロジェクト名>.SSISDeploymentManifest.xml というマニフェスト ファイルが作成され、プロジェクトのパッケージのコピーおよびパッケージの依存関係と共に、プロジェクトの bin\Deployment フォルダーまたは DeploymentOutputPath プロパティで指定された場所に格納されます。 マニフェスト ファイルには、プロジェクトに含まれるパッケージ、パッケージの構成、およびその他のファイルの一覧が記述されます。  
  
 配置フォルダーの内容は、プロジェクトをビルドするたびに更新されます。 つまり、このフォルダーに保存されているフォルダーのうち、ビルド プロセスで再度このフォルダーにコピーされなかったファイルはすべて、削除されます。 たとえば、配置フォルダーに保存されたパッケージ構成ファイルは削除されます。  
  
### パッケージ配置ユーティリティを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、パッケージ配置ユーティリティを作成する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトが含まれているソリューションを開きます。  
  
2.  プロジェクトを右クリックして、**[プロパティ]** をクリックします。  
  
3.  **[\<プロジェクト名> プロパティ ページ]** ダイアログ ボックスで、**[配置ユーティリティ]** をクリックします。  
  
4.  パッケージの配置時にパッケージの構成を更新するには、**[AllowConfigurationChanges]** を **True** に設定します。  
  
5.  **[CreateDeploymentUtility]** を **True** に設定します。  
  
6.  必要に応じて、**DeploymentOutputPath** プロパティを変更して、配置ユーティリティの場所を更新します。  
  
7.  **[OK]**をクリックします。  
  
8.  ソリューション エクスプローラーで、プロジェクトを右クリックし、**[ビルド]** をクリックします。  
  
9. ビルドの進捗状況とエラーが **[出力]** ウィンドウに表示されます。  
  
## 「  
 [パッケージ構成](../../integration-services/packages/package-configurations.md)   
 [パッケージ構成を作成する](../../integration-services/packages/create-package-configurations.md)   
 [配置ユーティリティを使用してパッケージを配置する](../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md)   
 [レガシー パッケージの配置 (SSIS)](../../integration-services/packages/legacy-package-deployment-ssis.md)  
  
  