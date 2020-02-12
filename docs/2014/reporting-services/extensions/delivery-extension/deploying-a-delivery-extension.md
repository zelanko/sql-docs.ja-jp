---
title: 配信拡張機能の配置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3b95fbb99affb91743d5b922f748cae5554736f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164415"
---
# <a name="deploying-a-delivery-extension"></a>配信拡張機能の配置
  配信拡張機能では、その構成情報を XML 構成ファイルの形式で指定します。 XML ファイルは、配信拡張機能に定義された XML スキーマに従います。 配信拡張機能により、構成ファイルを設定および変更するためのインフラストラクチャが提供されます。  
  
 配信拡張機能を置き換えたり、アップグレードしたりしても、配信拡張機能を参照するすべてのサブスクリプションは有効なままです。  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]配信拡張機能を作成して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]ライブラリにコンパイルした後、拡張機能を適切なディレクトリにコピーし、適切な[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]構成ファイルにエントリを追加して、レポートサーバーがそれを見つけられるようにする必要があります。  
  
## <a name="configuration-file-extension-element"></a>構成ファイルの Extension 要素  
 構成ファイルでは、レポート サーバーに配置する配信拡張機能を `Extension` 要素として入力する必要があります。 レポート サーバーの構成ファイルは、RSReportServer.config です。  
  
 次の表では、配信拡張機能の `Extension` 要素の属性について説明します。  
  
|Attribute|[説明]|  
|---------------|-----------------|  
|`Name`|拡張機能の一意な名前 (たとえば、電子メール配信拡張機能の場合は "レポート サーバーの電子メール"、ファイル共有配信拡張機能の場合は "レポート サーバーのファイル共有")。 
  `Name` 属性の最大文字数は 255 文字です。 名前は、構成ファイルの `Extension` 要素内のすべてのエントリの中で一意にする必要があります。 重複する名前がある場合には、レポート サーバーによってエラーが返されます。|  
|`Type`|アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。|  
|`Visible`|
  `false` の値は、配信拡張機能がユーザー インターフェイスに表示されないことを示します。 この属性が指定されない場合、既定値は `true` になります。|  
  
 RSReportServer.config ファイルの詳細については、「[Reporting Services 構成ファイル](../../report-server/reporting-services-configuration-files.md)」を参照してください。  
  
## <a name="deploying-the-extension-to-the-report-server"></a>レポート サーバーへの拡張機能の配置  
 レポート サーバーでは、通知またはレポートを処理して配信するために配信拡張機能を使用します。 レポート サーバーには、プライベート アセンブリとして配信拡張機能アセンブリを配置する必要があります。 また、レポート サーバーの構成ファイル RSReportServer.config にエントリを作成する必要もあります。  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>配信拡張機能アセンブリをレポート サーバーに配置するには  
  
1.  ステージング場所から、配信拡張機能を使用するレポート サーバーの bin ディレクトリにアセンブリをコピーします。 レポートサーバーの bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 です。\<InstanceName> \ Reporting ます。  
  
    > [!IMPORTANT]  
    >  既存の配信拡張機能アセンブリを上書きする場合、まず、レポート サーバー サービスを停止してから、更新済みのアセンブリをコピーする必要があります。 そのアセンブリをコピーした後で、サービスを再起動します。  
  
2.  アセンブリ ファイルをコピーした後、RSReportServer.config ファイルを開きます。 RSReportServer .config ファイルは、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 にあります。\<InstanceName> \ Reporting Services\ReportServer directory です。 配信拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。 またはメモ帳などの簡単[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]なテキストエディターを使用して、構成ファイルを開くことができます。  
  
3.  RSReportServer.config ファイルで `Delivery` 要素を探します。 新しく作成した配信拡張機能のエントリは、次の場所に作成する必要があります。  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  配信拡張機能のエントリを追加します。 エントリには、`Extension` および `Name` の値で構成される `Type` 要素を含める必要があります。このエントリは、次のようになります。  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     
  `Name` の値は、配信拡張機能の一意な名前です。 
  `Type` の値は、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> インターフェイスを実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧であり、その後にアセンブリの名前 (.dll ファイル拡張子は付けない) が続きます。 既定では、配信拡張機能が表示されます。 レポート マネージャーなどのユーザー インターフェイスで拡張機能を非表示にするには、`Visible` 属性を `Extension` 要素に追加し、それを `false` に設定します。  
  
5.  最後に、配信拡張機能の `FullTrust` 権限を与えるカスタム アセンブリのコード グループを追加します。 これを行うには、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 に既定で格納されている rssrvpolicy.config ファイルにコードグループを追加します。\<InstanceName> \ Reporting services\reportserver このコード グループは、次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     URL 構成要素は、配信拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。 
  [!INCLUDE[ssRS](../../../includes/ssrs.md)] のコード アクセス セキュリティの詳細については、「[セキュリティで保護された配置 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)」を参照してください。  
  
## <a name="deploying-the-extension-to-report-manager"></a>レポート マネージャーへの配信拡張機能の配置  
 配信拡張機能によって <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装した場合、レポート マネージャーの [サブスクリプション] ページで配信拡張機能を使用できます。 サブスクリプションのユーザー インターフェイスを有効にするには、拡張機能をレポート マネージャーに配置する必要があります。  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a>配信拡張機能アセンブリをレポート マネージャーに配置するには  
  
1.  ステージング場所からレポート マネージャーの bin ディレクトリにアセンブリをコピーします。 レポートマネージャー bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 です。\<InstanceName> \ Reporting services\reportmanager\bin です。  
  
2.  アセンブリ ファイルをコピーした後、RSReportServer.config ファイルを開きます。 RSReportServer .config ファイルは、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 にあります。\<InstanceName> \ Reporting Services\ReportServer directory です。 配信拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。 Visual&#xA0;Studio .NET またはメモ帳などの簡単なテキスト エディターを使用して、構成ファイルを開くことができます。  
  
3.  RSReportServer.config ファイルで `DeliveryUI` 要素を探します。 新しく作成した配信拡張機能のエントリは、次の場所に作成する必要があります。  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  配信拡張機能のエントリを追加します。 エントリには、と`Extension` `Name` `Type`の値を持つ要素が含まれている必要があり、次のようになります。  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     
  `Name` の値は、配信拡張機能の一意な名前です。 
  `Type` の値は、<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧であり、その後にアセンブリの名前 (.dll ファイル拡張子は付けない) が続きます。  
  
    > [!IMPORTANT]  
    >  
  `Name` 属性の値は、レポート サーバーとレポート マネージャーの両方の構成ファイルのエントリに対して同一にする必要があります。 それらのエントリが同一でない場合は、サーバー構成が無効になります。  
  
     最後に、配信拡張機能の `FullTrust` 権限を与えるカスタム アセンブリのコード グループを追加します。 これを行うには、コードグループを Rsmgrpolicy.config ファイルに追加します。このファイルは、既定では C:\Program の SQL Server \ MSRS10_50 にあります。\<InstanceName> \ Reporting services\reportmanager このコード グループは、次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     URL 構成要素は、配信拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。 の[!INCLUDE[ssRS](../../../includes/ssrs.md)]コードアクセスセキュリティの詳細については、「[セキュリティで保護された開発 &#40;Reporting Services](../secure-development/secure-development-reporting-services.md) 」を参照してください&#41;  
  
## <a name="verifying-the-deployment"></a>デプロイの確認  
 配信拡張機能が正常にレポート サーバーに配置されたかどうかを確認するには、Web サービスの <xref:ReportService2010.ReportingService2010.ListExtensions%2A> メソッドを使用します。 また、レポート マネージャーを開き、配信拡張機能がサブスクリプションに有効な配信拡張機能の一覧に含まれていることを確認する方法もあります。 レポートマネージャーとサブスクリプションの詳細については、「[サブスクリプションと配信 &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [配信拡張機能の実装](implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  
