---
title: "手順 2: 配置バンドルの確認 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20d8b11e28f7e26e5b61662d8340ab6dbfcc0b95
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-2-2---verifying-the-deployment-bundle"></a>レッスン 2-2-配置バンドルの確認
レッスン 1 では、Deployment Tutorial プロジェクトを作成し、パッケージと補助ファイルをプロジェクトに追加しました。前のタスクでプロジェクトの配置ユーティリティを構築しました。  
  
このタスクでは、配置バンドルの内容を確認します。 配置バンドルとは、目的のコンピューターにコピーしてパッケージのインストールに使用するフォルダーです。 配置ユーティリティの場所として既定値の bin\Deployment を使用した場合は、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの Deployment Tutorial フォルダー内にある Bin\Deployment フォルダーが配置バンドルです。  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a>配置バンドルの内容を確認するには  
  
1.  コンピューターで bin\Deployment フォルダーを見つけます。  
  
2.  次のファイルがあることを確認します。  
  
    -   DataTransfer.dtsx  
  
    -   datatransferconfig.dtsconfig  
  
    -   Deployment Tutorial.SSISDeploymentManifest  
  
    -   LoadXMLData.dtsx  
  
    -   loadxmldataconfig.dtsconfig  
  
    -   NewCustomers.txt  
  
    -   orders.xml  
  
    -   orders.xsd  
  
    -   Readme.txt  
  
3.  [Deployment Tutorial.SSISDeploymentManifest] を右クリックし、 **[ファイルを開くアプリケーションの選択]**をポイントして、 **[Internet Explorer]**をクリックします。 メモ帳などのテキスト エディターでもファイルを開くことができます。 ファイルの XML コードは次のようになっています。  
  
    `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  **AllowConfigurationChanges** 属性の値が **true** であること、2 つの各パッケージの **Package** 要素、パッケージでない 4 つの各ファイルの **MiscellaneousFile** 要素、および 2 つの各 XML 構成ファイルの **ConfigurationFile** 要素が XML に含まれていることを確認します。  
  
5.  Internet Explorer またはテキスト エディターを終了します。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 3: SSIS パッケージのインストール](../integration-services/lesson-3-install-ssis-packages.md)  
  
  
  

