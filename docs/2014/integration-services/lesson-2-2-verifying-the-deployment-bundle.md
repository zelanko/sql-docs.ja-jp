---
title: '手順 2: 配置バンドルの確認 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5a9f5ef250617b445ce30624537f715be73b3d2f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102122"
---
# <a name="step-2-verifying-the-deployment-bundle"></a>手順 2: 配置バンドルの確認
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
  
3.  [Deployment Tutorial.SSISDeploymentManifest] を右クリックし、 **[ファイルを開くアプリケーションの選択]** をポイントして、 **[Internet Explorer]** をクリックします。 メモ帳などのテキスト エディターでもファイルを開くことができます。 ファイルの XML コードは次のようになっています。  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  いることを確認の値、`AllowConfigurationChanges`属性が**true** XML に含まれて、`Package`の 2 つのパッケージの各要素を`MiscellaneousFile`パッケージ以外の 4 つのファイルの各要素と`ConfigurationFile`それぞれの 2 つの XML 構成ファイルの要素です。  
  
5.  Internet Explorer またはテキスト エディターを終了します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 3: パッケージのインストール](../integration-services/lesson-3-install-ssis-package.md)  
  
![Integration Services のアイコン (小)](media/dts-16.gif "Integration Services アイコン (小)")**Integration Services の日付を維持します。** <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
  
