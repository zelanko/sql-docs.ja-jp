---
title: "方法: レポート サーバーにデータ処理拡張機能の配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
caps.latest.revision: 45
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ed23ebf2bd6cbecbd028488c5188368e1a076d46
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="deploying-a-data-processing-extension-to-a-report-server"></a>レポート サーバーにデータ処理拡張機能の配置
  レポート サーバーは、表示レポートのデータを取得および処理するためにデータ処理拡張機能を使用します。 データ処理拡張機能のアセンブリは、プライベート アセンブリとしてレポート サーバーに配置してください。 また、レポート サーバーの構成ファイル RSReportServer.config にエントリを作成する必要もあります。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>データ処理拡張機能のアセンブリを配置するには  
  
1.  ステージング場所から、データ処理拡張機能を使用するレポート サーバーの bin ディレクトリにアセンブリをコピーします。 レポート サーバーの bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL server \msrs10_50. です。\<*インスタンス名*> \Reporting Services\ReportServer\bin です。  
  
    > [!NOTE]  
    >  この手順により、SQL Server の新しいインスタンスへのアップグレードが回避されます。 詳細については、「 [Upgrade and Migrate Reporting Services](../../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。  
  
2.  アセンブリ ファイルをコピーした後、RSReportServer.config ファイルを開きます。 RSReportServer.config ファイルは、ReportServer ディレクトリにあります。 データ処理拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。 Visual Studio またはメモ帳などの単純なテキスト エディターで、構成ファイルを開くことができます。  
  
3.  RSReportServer.config ファイルで **Data** 要素を探します。 新しく作成したデータ処理拡張機能のエントリは、次の場所に作成する必要があります。  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  データ処理拡張機能のエントリを追加します。 エントリを含める必要があります、**拡張子**の値を持つ要素**名前**と**型**し、次のようになります。  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     値は、**名前**データ処理拡張機能の一意の名前を指定します。 値は、**型**を実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧には、<xref:Microsoft.ReportingServices.Interfaces.IExtension>と<xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>インターフェイス、続けて、アセンブリ (.dll ファイル拡張子を含まない) の名前。 既定では、データ処理拡張機能が表示されます。 レポート マネージャーなどのユーザー インターフェイスで拡張機能を非表示にするには、 **Extension** 要素に **Visible** 属性を追加して、 **false**に設定します。  
  
5.  付与するカスタム アセンブリのコード グループを追加**FullTrust**拡張機能のアクセスを許可します。 既定では %ProgramFiles%\Microsoft SQL Server にある rssrvpolicy.config ファイルにコード グループを追加することで、これを行う\\< MSRS10_50\< 。*インスタンス名*> \reporting です。 このコード グループは、次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL 構成要素は、データ処理拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。 コード アクセス セキュリティの詳細については[!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]を参照してください[セキュリティで保護された開発 & #40 です。Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>展開の確認  
 データ処理拡張機能がレポート サーバーに正常に配置されたかどうかを確認するには、Web サービス <xref:ReportService2010.ReportingService2010.ListExtensions%2A> メソッドを使用します。 レポート マネージャーを開いて、拡張機能が使用可能なデータ ソース一覧に含まれていることを確認することもできます。 レポート マネージャーとデータ ソースの詳細については、「[共有データ ソースを作成、変更、および削除する &#40;SSRS&#41;](../../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [データ処理拡張機能の配置](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
