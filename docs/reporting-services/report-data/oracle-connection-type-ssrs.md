---
title: Oracle の接続の種類 (レポート ビルダー、Power BI Report Server) | Microsoft Docs
ms.date: 01/16/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c2e9ee78c6a033443b960ba972b74be2a1e6aebd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081737"
---
# <a name="oracle-connection-type-report-builder--power-bi-report-server--microsoft-docs"></a>Oracle の接続の種類 (レポート ビルダー、Power BI Report Server) | Microsoft Docs

Oracle データベースのデータをレポート内で使用するには、種類が Oracle のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、Oracle Data Provider を直接使用し、Oracle クライアント ソフトウェア コンポーネントが必要です。 この記事では、Reporting Services、Power BI Report Server、およびレポート ビルダーのドライバーをダウンロードしてインストールする方法について説明します。

## <a name="64-bit-drivers-for-the-report-servers"></a>レポート サーバー用の 64 ビット ドライバー

Power BI Report Server と SQL Server Reporting Services 2016 および 2017 には、いずれも Managed ODP.NET が使用されます。 次の手順は、最新の 18x ドライバーを使用する場合にのみ必要です。 これらのファイルは c:\oracle64 にインストールされていることを前提としています。

1. Oracle ダウンロード サイトで、[Oracle 64-bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdeploy-4242173.html) をインストールします。 
2. ODP.NET Managed Client を GAC に登録します。C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. ODP.NET Managed Client エントリを machine.config に追加します。C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="power-bi-reports-use-unmanaged-odpnet"></a>Power BI レポートに Unmanaged ODP.NET を使用する

Power BI レポートには **Unmanaged ODP.NET** が使用されます。 次の手順に従って、Unmanaged ODP.NET を登録します。

1. ODP.NET Unmanaged Client を GAC に登録します。

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. ODP.NET Unmanaged Client エントリを machine.config に追加します。

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
 
## <a name="32-bit-drivers-for-report-builder"></a>レポート ビルダー用の 32 ビット ドライバー

次の手順は、最新の 18x ドライバーを使用する場合にのみ必要です。 これらのファイルは c:\oracle32 にインストールされていることを前提としています。

1. Oracle ダウンロード サイトで、[Oracle 32-bit ODAC Oracle Universal Installer (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdev-4242174.html) をインストールします。
2. ODP.NET Managed Client を GAC に登録します。C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. ODP.NET Managed Client エントリを machine.config に追加します。C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="power-bi-reports-use-unmanaged-odpnet"></a>Power BI レポートに Unmanaged ODP.NET を使用する  

Power BI レポートには **Unmanaged ODP.NET** が使用されます。 次の手順に従って、Unmanaged ODP.NET を登録します。

1. ODP.NET Unmanaged Client を GAC に登録します。

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. ODP.NET Unmanaged Client エントリを machine.config に追加します。

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
 

 このトピックの情報を使用して、データ ソースを構築してください。 手順については、「 [データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a> 接続文字列  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次に示す接続文字列の例では、Unicode を使用して "Oracle18" というサーバー上の Oracle データベースを指定しています。 サーバー名は、Tnsnames.ora 構成ファイルで Oracle サーバー インスタンス名として定義されたものと一致する必要があります。  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
 接続文字列の例の詳細については、「[データ接続文字列を作成する - レポート ビルダーおよび SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、「 [レポート データ ソースに関する資格情報と接続情報を指定する](specify-credential-and-connection-information-for-report-data-sources.md)」をご覧ください。  
  
  
##  <a name="Query"></a> クエリ  
 データセットを作成するには、ボックスの一覧からストアド プロシージャを選択するか、SQL クエリを作成します。 クエリを作成するには、テキストベースのクエリ デザイナーを使用する必要があります。 詳細については、「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md)」を参照してください。  
  
 結果セットを 1 つだけ返すストアド プロシージャを指定できます。 カーソルベースのクエリの使用はサポートされていません。  
  
##  <a name="Parameters"></a> パラメーター  
 クエリにクエリ変数が含まれている場合は、対応するレポート パラメーターが自動的に生成されます。 この拡張機能では、名前付きパラメーターがサポートされます。 Oracle Version 9 以降の場合、複数値パラメーターがサポートされます。  
  
 レポート パラメーターは、既定のプロパティ値を使用して作成されます。この既定のプロパティ値は、変更が必要になることがあります。 たとえば、各レポート パラメーターのデータ型は **Text**です。 レポート パラメーターを作成した後に、既定値の変更が必要になる場合があります。 詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)にあります。  
  
  
##  <a name="Remarks"></a> 解説  
 Oracle データ ソースに接続するには、システム管理者が、Oracle データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Oracle をインストールしておく必要があります。 このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。  
  
 詳細については、次の記事を参照してください。  
  
-   [Reporting Services を使用して Oracle データ ソースの構成およびアクセスを行う方法](https://support.microsoft.com/kb/834305)  
-   [NETWORK SERVICE セキュリティ プリンシパルに権限を追加する方法](https://support.microsoft.com/kb/870668)  
  
### <a name="alternate-data-extensions"></a>代替データ拡張機能 
 
 Oracle データベースからのデータの取得は、OLE DB のデータ ソースの種類を使用して行うこともできます。 詳細については、「[OLE DB の接続の種類 &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md)」を参照してください。  

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions" 
### <a name="report-models"></a>レポート モデル  

 Oracle データベースに基づくモデルを作成することもできます。  
::: moniker-end
   
### <a name="platform-and-version-information"></a>プラットフォームおよびバージョン情報  

 プラットフォームとバージョンのサポートについて詳しくは、「[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)」をご覧ください。  

  
## <a name="see-also"></a>参照

 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
