---
title: 標準 .NET Framework データ プロバイダーを登録する (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
caps.latest.revision: 17
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fcfaa1e1459df5bd3a399ce80b29dfd6a721e991
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085164"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a>標準 .NET Framework データ プロバイダーを登録する (SSRS)
  サード パーティの [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート データセット用のデータを取得するには、レポート作成クライアントとレポート サーバーの 2 か所に [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー アセンブリを配置し、登録する必要があります。 レポート作成クライアントでは、データ プロバイダーをデータ ソースの種類として登録し、それをクエリ デザイナーに関連付ける必要があります。 これにより、レポート データセットを作成する際に、データ ソースの種類としてこのデータ プロバイダーを選択できるようになります。 関連付けられているクエリ デザイナーが開き、それを利用してこのデータ ソースの種類に対するクエリを作成することができます。 レポート サーバーでは、データ プロバイダーをデータ ソースの種類として登録する必要があります。 そうすることで、このデータ プロバイダーを使用してデータ ソースからデータを取得するパブリッシュ済みレポートを処理することができます。  
  
 サード パーティのデータ プロバイダーには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能で使用できるすべての機能が用意されているわけではありません。 詳細については、「[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)」をご覧ください。 .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーの機能の拡張については、「 [データ処理拡張機能の実装](../extensions/data-processing/implementing-a-data-processing-extension.md)」をご覧ください。  
  
 データ プロバイダーのインストールと登録を行うには、管理者の資格情報が必要です。  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a>レポート サーバーへの .NET Framework データ プロバイダーの登録  
 この [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーをレポート サーバーで使用するパブリッシュ済みレポートを処理するには、レポート サーバーにアセンブリをインストールする必要があります。 それには 2 つの構成ファイルを変更します。 データ プロバイダーを登録するには、rsreportserver.config を変更します。 アセンブリにコード アクセス セキュリティ権限を許可するには、rssrvpolicy.config を変更します。  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a>レポート サーバーにデータ プロバイダー アセンブリをインストールするには  
  
1.  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを使用するレポート サーバーの bin ディレクトリの既定の場所に移動します。 レポート サーバーの bin ディレクトリの既定の場所は、*\<drive>*:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin です。  
  
2.  ステージング場所からレポート サーバーの bin ディレクトリに、アセンブリをコピーします。 または、グローバル アセンブリ キャッシュ (GAC) にアセンブリを読み込みます。 詳細については、MSDN の [SDK ドキュメントの「](http://go.microsoft.com/fwlink/?linkid=63912) アセンブリとグローバル アセンブリ キャッシュの使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 」をご覧ください。  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a>レポート サーバーに .NET データ プロバイダーを登録するには  
  
1.  bin の親ディレクトリ ReportServer に、RSReportServer.config ファイルのバックアップを作成します。  
  
2.  RSReportServer.config を開きます。構成ファイルを開くことができます[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]またはメモ帳などの単純なテキスト エディター。  
  
3.  検索、 `Data` RSReportServer.config ファイル内の要素。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー用のエントリは、次の場所に作成されます。  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー用のエントリを追加します。  
  
    |属性|説明|  
    |---------------|-----------------|  
    |`Name`|データ プロバイダーの固有名を入力します (たとえば「 **MyNETDataProvider**」など)。 `Name` 属性の最大文字数は 255 文字です。 名前は内のすべてのエントリの中で一意である必要があります、`Extension`構成ファイルの要素。 ここで指定した値は、新しいデータ ソースを作成する際にデータ ソースの種類を示すドロップダウン リストに表示されます。|  
    |`Type`|<xref:System.Data.IDbConnection> インターフェイスを実装するクラスの完全修飾名前空間と、その後に [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー アセンブリの名前 (.dll ファイル名拡張子を含まない) を指定する、コンマ区切りのリストを入力します。|  
  
     たとえば、DLL に関する次のようなエントリがレポート サーバーの bin ディレクトリに配置されているとします。  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     アセンブリをグローバル アセンブリ キャッシュ (GAC) に読み込む場合、厳密な名前のプロパティを指定する必要があります。 以下に例を示します。  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a>.NET データ プロバイダーのコード グループ ポリシーを設定するには  
  
1.  bin の親ディレクトリ ReportServer に、rssrvpolicy.config ファイルのバックアップ コピーを作成します。  
  
2.  rssrvpolicy.config を開きます。[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] またはメモ帳などの簡単なテキスト エディターを使用して、構成ファイルを開くことができます。  
  
3.  rssrvpolicy.config ファイル内で `CodeGroup` 要素を探します。  
  
4.  付与するデータ プロバイダー アセンブリのコード グループを追加`FullTrust`権限です。 コード グループは次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL メンバーシップは、多くのメンバーシップ条件の中からデータ プロバイダー用に選択した 1 つのみになります。  
  
### <a name="verifying-the-deployment-and-registration"></a>配置と登録の検証  
 レポート マネージャーを開き、データ プロバイダーが使用可能なデータ ソースの一覧に含まれていることを確認することで、データ プロバイダーがレポート サーバーに正常に配置されたかどうかを検証できます。 レポート マネージャーとデータ ソースの詳細については、「[共有データ ソースを作成、変更、および削除する &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)」を参照してください。  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a>レポート デザイナー クライアントへの .NET Framework データ プロバイダーの登録  
 この [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーをデータ ソースとして使用するレポートを作成するには、レポート デザイナーが実行されているクライアント コンピューターにアセンブリをインストールする必要があります。 それには 2 つの構成ファイルを変更します。 データ ソースとしてデータ プロバイダーを登録し、汎用クエリ デザイナーを使用できるようにするには、RSReportDesigner.config を変更します。 データ プロバイダー アセンブリにコード アクセス セキュリティ権限を許可するには、RSPreviewPolicy.config を変更します。  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a>レポート デザイナー クライアントにデータ プロバイダー アセンブリをインストールするには  
  
1.  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを使用するレポート デザイナー クライアントの PrivateAssemblies ディレクトリの既定の場所に移動します。 PrivateAssemblies ディレクトリの既定の場所は、*\<drive>*:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。  
  
2.  ステージング場所からレポート デザイナー クライアントの PrivateAssemblies ディレクトリに、アセンブリをコピーします。 または、グローバル アセンブリ キャッシュ (GAC) にアセンブリを読み込みます。 詳細については、MSDN の [SDK ドキュメントの「](http://go.microsoft.com/fwlink/?linkid=63912) アセンブリとグローバル アセンブリ キャッシュの使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 」をご覧ください。  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a>レポート デザイナー クライアントに .NET データ プロバイダーを登録するには  
  
1.  PrivateAssemblies ディレクトリに RSReportDesigner.config ファイルのバックアップ コピーを作成します。  
  
2.  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] またはメモ帳などの簡単なテキスト エディターを使用して、RSReportDesigner.config を開きます。  
  
3.  RSReportDesigner.config ファイル内で `Data` 要素を探します。 データ プロバイダー用のエントリは、次の場所に作成されます。  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  データ プロバイダーのエントリを追加します。  
  
    |属性|説明|  
    |---------------|-----------------|  
    |`Name`|データ プロバイダーの固有名を入力します (たとえば「 **MyNETDataProvider**」など)。 `Name` 属性の最大文字数は 255 文字です。 名前は内のすべてのエントリの中で一意である必要があります、`Extension`構成ファイルの要素。 ここで指定した値は、新しいデータ ソースを作成する際にデータ ソースの種類を示すドロップダウン リストに表示されます。|  
    |`Type`|<xref:System.Data.IDbConnection> インターフェイスを実装するクラスの完全修飾名前空間と、その後に [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー アセンブリの名前 (.dll ファイル名拡張子を含まない) を指定する、コンマ区切りのリストを入力します。|  
  
     たとえば、DLL に関する次のようなエントリが [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の PrivateAssemblies ディレクトリに配置されているとします。  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     アセンブリを GAC に読み込む場合、厳密な名前のプロパティを指定する必要があります。 以下に例を示します。  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  RSReportDesigner.config ファイル内で `Designer` 要素を探します。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー用のエントリは、次の場所に作成されます。  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  RSReportDesigner.config ファイルの下に次のエントリを追加、`Designer`要素。 のみを交換する必要があります、`Name`前のエントリで指定した名前の属性です。  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a>レポート デザイナー クライアントにおける .NET データ プロバイダーのコード グループ ポリシーを設定するには  
  
1.  PrivateAssemblies ディレクトリに RSPreviewPolicy.config ファイルのバックアップ コピーを作成します。  
  
2.  RSPreviewPolicy.config を開きます[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]またはメモ帳などの単純なテキスト エディター。  
  
3.  RSPreviewPolicy.config ファイル内で `CodeGroup` 要素を探します。  
  
4.  コード グループを追加する、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]付与するデータ プロバイダー アセンブリ`FullTrust`権限です。 コード グループは次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL メンバーシップは、多くのメンバーシップ条件の中からデータ プロバイダー用に選択した 1 つのみになります。  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a>レポート デザイナー クライアントでの配置と登録の検証  
 配置を検証するには、ローカル コンピューターの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインスタンスをすべて閉じておく必要があります。 現在のすべてのセッションを終了すると後、かどうか、データ プロバイダーが正常に展開レポート デザイナーで新しいレポート プロジェクトを作成することでを確認できます[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]です。 レポートの新しいデータセットを作成するときに、使用可能なデータ ソースの種類にそのデータ プロバイダーが含まれている必要があります。  
  
## <a name="platform-considerations"></a>プラットフォームに関する注意点  
 64 ビット (x64) プラットフォームでは、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] は 32 ビット WOW モードで動作します。 x64 プラットフォームでレポートを作成する場合、レポートをプレビューするためには、レポート作成クライアントに 32 ビットのデータ プロバイダーをインストールする必要があります。 同じシステムでレポートをパブリッシュした場合、レポート マネージャーでレポートを表示するためには x64 データ プロバイダーが必要になります。  
  
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] ベースのプラットフォームでは、[!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] がサポートされません。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共にインストールするデータ処理拡張機能は、各プラットフォーム用にネイティブでコンパイルし、正しい場所にインストールする必要があります。 カスタム データ プロバイダーまたは標準の [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを登録する場合、適切なプラットフォーム用にネイティブでコンパイルし、適切な場所にインストールする必要があります。 32 ビット プラットフォームで実行する場合、データ プロバイダーを 32 ビット プラットフォーム用にコンパイルする必要があります。 64 ビット プラットフォームで実行する場合、データ プロバイダーを 64 ビット プラットフォーム用にコンパイルする必要があります。 64 ビット インターフェイスでラップした 32 ビット データ プロバイダーを 64 ビット プラットフォームで使用することはできません。 サード パーティ ソフトウェアを確認して、データ プロバイダーがインストール先のプラットフォームで動作するかどうか調べてください。 データ プロバイダーとプラットフォームのサポートの詳細については、「[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [データ処理拡張機能の実装](../extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md)   
 [Reporting Services のコード アクセス セキュリティ](../extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  