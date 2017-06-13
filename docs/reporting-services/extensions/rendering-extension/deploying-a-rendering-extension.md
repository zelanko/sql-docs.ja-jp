---
title: "表示拡張機能を展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
caps.latest.revision: 44
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 260e104d2686ab9111c9b38c2ecf6c5da2fbdb91
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="deploying-a-rendering-extension"></a>表示拡張機能の配置
  書き込み、コンパイルした後、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]レポートに表示拡張機能、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]ライブラリ、およびレポート デザイナー、レポート サーバーで検出できるようにする必要があります。 それには、拡張機能を適切なディレクトリにコピーし、適切な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルにエントリを追加します。  
  
## <a name="configuration-file-rendering-extension-element"></a>構成ファイルの表示拡張機能要素  
 表示拡張機能を .DLL にコンパイルした後、rsreportserver.config ファイルにエントリを追加します。 既定では、場所は、%ProgramFiles%\Microsoft SQL server \msrs10_50. です。\<InstanceName > \reporting です。 親要素は\<レンダリング >。 Render 要素の下には、各表示拡張機能の Extension 要素があります。 **Extension** 要素には、Name と Type という 2 つの属性があります。  
  
 次の表では、表示拡張機能の **Extension** 要素の属性について説明します。  
  
|属性|Description|  
|---------------|-----------------|  
|**名前**|拡張機能の一意の名前。 **Name** 属性の最大文字数は 255 文字です。 名前は、構成ファイルの **Extensions** 要素内のすべてのエントリの中で一意にする必要があります。 重複する名前がある場合には、レポート サーバーによってエラーが返されます。|  
|**型**|アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。|  
|**[表示]**|値が **false** の場合、表示拡張機能がユーザー インターフェイスに表示されないことを示します。 この属性が指定されない場合、既定値は **true**になります。|  
|**LogAllExecutionRequests**|値が **false** の場合、エントリがログに記録されるのは、セッションでレポートが最初に実行されるときのみであることを示します。 この属性が指定されない場合、既定値は **true**になります。<br /><br /> この設定によって、レポートに最初に表示されるページについてのみエントリをログに記録するか ( **false**の場合)、レポートに表示されるページごとにエントリをログに記録するか ( **true**の場合) が決まります。|  
  
 詳細については、「 [RsReportServer.config 構成ファイル](../../../reporting-services/report-server/rsreportserver-config-configuration-file.md)」を参照してください。  
  
## <a name="deploying-the-extension-to-the-report-server"></a>レポート サーバーへの拡張機能の配置  
 レポート サーバーでは、レポートを他の形式にエクスポートするとき、表示拡張機能を使用します。 レポート サーバーにプライベート アセンブリとして表示拡張機能アセンブリを配置する必要があります。 また、レポート サーバーの構成ファイル rsreportserver.config にエントリを作成する必要もあります。  
  
### <a name="to-deploy-the-assembly"></a>アセンブリを配置するには  
  
1.  ステージング場所から、表示拡張機能を使用するレポート サーバーの bin ディレクトリにアセンブリをコピーします。 レポート サーバーの Bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL server \msrs10_50. です。\<InstanceName > \Reporting Services\ReportServer\Bin です。  
  
2.  アセンブリ ファイルをコピーした後、rsreportserver.config ファイルを開きます。 rsreportserver.config ファイルもレポート サーバーの bin ディレクトリにあります。 構成ファイルに拡張機能アセンブリ ファイルのエントリを作成する必要があります。 使用してファイルを開くことができます[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]または単純なテキスト エディター。  
  
     詳細については、「 [RsReportServer.config 構成ファイル](../../../reporting-services/report-server/rsreportserver-config-configuration-file.md)」を参照してください。  
  
3.  Rsreportserver.config ファイルで **Render** 要素を探します。 新しく作成した拡張機能のエントリは、次の場所に作成する必要があります。  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  表示拡張機能のエントリを追加します。 エントリには、 **Name** および **Type**の値で構成される要素を含める必要があります。このエントリは次のようになります。  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     **Name** の値は、表示拡張機能の一意な名前です。 値は、**型**の完全修飾名前空間のエントリを含むコンマ区切りの一覧には、<xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>実装では、続けて、アセンブリ (.dll ファイル拡張子を含まない) の名前。 既定では、表示拡張機能が表示されます。 レポート マネージャーなどのユーザー インターフェイスで拡張機能を非表示にするには、 **Extension** 要素に **Visible** 属性を追加して、 **false**に設定します。  
  
## <a name="verifying-the-deployment"></a>配置の確認  
 また、レポート マネージャーを開き、配信拡張機能がレポートに有効なエクスポートの種類の一覧に含まれていることを確認することもできます。  
  
## <a name="see-also"></a>参照  
 [表示拡張機能を実装します。](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [表示拡張機能の概要](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [IRenderingExtension インターフェイスの実装](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [セキュリティ拡張機能に関する考慮事項](../../../reporting-services/extensions/security-considerations-for-extensions.md)  
  
  
