---
title: "方法: レポート デザイナーにデータ処理拡張機能の配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
caps.latest.revision: 41
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e5e309ee7092bdc64efa89fa27579e9e8944da14
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="deploying-a-data-processing-extension-to-report-designer"></a>レポート デザイナーにデータ処理拡張機能の配置
  レポートを設計する際、レポート デザイナーは、データ処理拡張機能を使用してデータを取得し、処理します。 データ処理拡張機能アセンブリは、プライベート アセンブリとしてレポート デザイナーに配置する必要があります。 さらに、レポート デザイナー構成ファイル RSReportDesigner.config にエントリを作成する必要があります。  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>データ処理拡張機能のアセンブリを配置するには  
  
1.  ステージング場所から Report Designer ディレクトリにアセンブリをコピーします。 Report Designer ディレクトリの既定の場所は、C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。  
  
2.  アセンブリ ファイルをコピーした後、RSReportDesigner.config ファイルを開きます。 RSReportDesigner.config ファイルも Report Designer ディレクトリにあります。 データ処理拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。 構成ファイルを開くことができます[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]またはメモ帳などの単純なテキスト エディターを使用します。  
  
3.  RSReportDesigner.config ファイルで **Data** 要素を探します。 新しく作成したデータ処理拡張機能のエントリは、次の場所に作成する必要があります。  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  エントリが含まれているデータ処理拡張機能を追加、**拡張子**の値を持つ要素、**名前**、**型**、および**Visible**属性。 このエントリは、次のようになります。  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     値は、**名前**データ処理拡張機能の一意の名前を指定します。 値は、**型**を実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧には、<xref:Microsoft.ReportingServices.Interfaces.IExtension>と<xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>インターフェイス、続けて、アセンブリ (.dll ファイル拡張子を含まない) の名前。 既定では、データ処理拡張機能が表示されます。 レポート デザイナーなどのユーザー インターフェイスで拡張機能を非表示にするには追加、 **Visible**属性を**拡張子**要素に設定し、 **false**です。  
  
5.  最後に、許可するカスタム アセンブリのコード グループを追加**FullTrust**拡張機能のアクセスを許可します。 これを行うには、既定では C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies にある rspreviewpolicy.config ファイルにコード グループを追加します。 このコード グループは、次のようになります。  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL 構成要素は、データ処理拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。 コード アクセス セキュリティの詳細については[!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)]を参照してください[セキュリティで保護された開発 & #40 です。Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
## <a name="generic-query-designer"></a>汎用クエリ デザイナー  
 レポート デザイナーには、カスタム データ処理拡張機能で使用できる汎用クエリ デザイナーが用意されています。 このデザイナーは、クエリ ペインと結果ペインの 2 つのペインで構成されます。 この汎用デザイナーは、上記のグラフィカル インターフェイスでサポートされていないクエリの記述に使用できます。 グラフィカル クエリ デザイナーと異なり、汎用クエリ デザイナーでは、クエリ構文のチェックやクエリの再構成は行われません。  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a>カスタム拡張機能で汎用クエリ デザイナーを有効にするには  
  
-   RSReportDesigner.config ファイルの下に次のエントリを追加、**デザイナー**要素、置換、**名前**前のエントリで指定した名前の属性です。  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a>展開の確認  
 配置を検証するには、ローカル コンピューターの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインスタンスをすべて閉じておく必要があります。 現在のセッションをすべて終了したら、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で新しいレポート プロジェクトを作成します。これによって、データ処理拡張機能がレポート デザイナーに正常に配置されたかどうかを確認できます。 レポート用の新しいデータセットを作成するとき、使用可能なデータ ソースの種類の一覧に新しい拡張機能が表示されます。  
  
## <a name="see-also"></a>参照  
 [データ処理拡張機能の配置](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
