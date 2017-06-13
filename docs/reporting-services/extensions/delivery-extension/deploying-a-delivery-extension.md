---
title: "配信拡張機能の配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d072577828375a08c133bb1a68d93e652e5cf168
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="deploying-a-delivery-extension"></a>配信拡張機能の配置
  配信拡張機能では、その構成情報を XML 構成ファイルの形式で指定します。 XML ファイルは、配信拡張機能に定義された XML スキーマに従います。 配信拡張機能により、構成ファイルを設定および変更するためのインフラストラクチャが提供されます。  
  
 配信拡張機能を置き換えたり、アップグレードしたりしても、配信拡張機能を参照するすべてのサブスクリプションは有効なままです。  
  
 書き込み、コンパイルした後、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]配信拡張機能を[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]ライブラリ、適切なディレクトリに、拡張機能をコピーし、適切なエントリを追加する必要があります[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]構成ファイルのため、レポート サーバーで見つけることができます。  
  
## <a name="configuration-file-extension-element"></a>構成ファイルの Extension 要素  
 レポート サーバーに配置する配信拡張機能として入力する必要がある**拡張子**構成ファイル内の要素。 レポート サーバーの構成ファイルは、RSReportServer.config です。  
  
 次の表に、属性、**拡張子**配信拡張機能の要素。  
  
|属性|Description|  
|---------------|-----------------|  
|**名前**|拡張機能の一意な名前 (たとえば、電子メール配信拡張機能の場合は "レポート サーバーの電子メール"、ファイル共有配信拡張機能の場合は "レポート サーバーのファイル共有")。 **Name** 属性の最大文字数は 255 文字です。 名前は、構成ファイルの **Extension** 要素内にあるすべてのエントリの間で一意にする必要があります。 重複する名前がある場合には、レポート サーバーによってエラーが返されます。|  
|**型**|アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。|  
|**[表示]**|値**false**配信拡張機能が表示されないことのユーザー インターフェイスでことを示します。 この属性が指定されない場合、既定値は **true**になります。|  
  
 RSReportServer.config ファイルの詳細については、次を参照してください。 [Reporting Services の構成ファイル](../../../reporting-services/report-server/reporting-services-configuration-files.md)です。  
  
## <a name="deploying-the-extension-to-the-report-server"></a>レポート サーバーへの拡張機能の配置  
 レポート サーバーでは、通知またはレポートを処理して配信するために配信拡張機能を使用します。 レポート サーバーには、プライベート アセンブリとして配信拡張機能アセンブリを配置する必要があります。 また、レポート サーバーの構成ファイル RSReportServer.config にエントリを作成する必要もあります。  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>配信拡張機能アセンブリをレポート サーバーに配置するには  
  
1.  ステージング場所から、配信拡張機能を使用するレポート サーバーの bin ディレクトリにアセンブリをコピーします。 レポート サーバーの bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL Server\MSRS13 です。\<InstanceName > \Reporting Services\ReportServer\bin です。  
  
    > [!IMPORTANT]  
    >  既存の配信拡張機能アセンブリを上書きする場合、まず、レポート サーバー サービスを停止してから、更新済みのアセンブリをコピーする必要があります。 そのアセンブリをコピーした後で、サービスを再起動します。  
  
2.  アセンブリ ファイルをコピーした後、RSReportServer.config ファイルを開きます。 RSReportServer.config ファイルは %ProgramFiles%\Microsoft SQL Server\MSRS13 にあります。\<InstanceName > \reporting ディレクトリ。 配信拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。 構成ファイルを開くことができます[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]またはメモ帳などの単純なテキスト エディター。  
  
3.  検索、**配信**RSReportServer.config ファイル内の要素。 新しく作成した配信拡張機能のエントリは、次の場所に作成する必要があります。  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  配信拡張機能のエントリを追加します。 エントリを含める必要があります、**拡張子**の値を持つ要素**名前**と**型**、し、次のようになります。  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     値は、**名前**配信拡張機能の一意の名前を指定します。 値は、**型**を実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧には、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>インターフェイス、続けて、アセンブリ (.dll ファイル拡張子を含まない) の名前。 既定では、配信拡張機能が表示されます。 Web ポータルなどのユーザー インターフェイスで拡張機能を非表示にするには追加、 **Visible**属性を**拡張子**要素に設定し、 **false**です。  
  
5.  最後に、許可するカスタム アセンブリのコード グループを追加**FullTrust**配信拡張機能に対するアクセス許可。 既定では %ProgramFiles%\Microsoft SQL Server\MSRS13 内にある rssrvpolicy.config ファイルにコード グループを追加する。 これを行います。\<InstanceName > \reporting です。 このコード グループは、次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS13.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     URL 構成要素は、配信拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。 コード アクセス セキュリティの詳細については[!INCLUDE[ssRS](../../../includes/ssrs-md.md)]を参照してください[。開発 &#40; をセキュリティで保護します。Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
   
## <a name="verifying-the-deployment"></a>展開の確認  
 配信拡張機能が正常にレポート サーバーに配置されたかどうかを確認するには、Web サービスの <xref:ReportService2010.ReportingService2010.ListExtensions%2A> メソッドを使用します。 Web ポータルを開き、サブスクリプションの利用可能な配信拡張機能の一覧で、拡張機能が含まれていることを確認できますも。 Web ポータルとサブスクリプションに関する詳細については、次を参照してください。[サブスクリプションと配信 & #40 です。Reporting Services &#41;](../../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>参照  
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

