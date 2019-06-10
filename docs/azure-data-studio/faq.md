---
title: FAQ
titleSuffix: Azure Data Studio
description: Azure Data Studio についてよく寄せられる質問 (FAQ)。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 7bd6c42882c9adc938904621b7939bea1b0e68de
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800748"
---
# <a name="includeazure-data-studioincludesname-sosmd-faq"></a>[!INCLUDE[Azure Data Studio](../includes/name-sos.md)] FAQ

## <a name="what-is-azure-data-studio"></a>Azure Data Studio とは何ですか。

Azure Data Studio は新しいオープン ソース、オンプレミスでの Azure のデータのファミリを使用してデータのプロフェッショナル向けのクロスプラット フォーム対応のデスクトップ環境とクラウドの Windows、MacOS、Linux でのデータ プラットフォームです。 SQL Operations Studio のプレビューの名前でリリースされていた、Azure Data Studio プランの最新のエディターを使用したエクスペリエンス処理が非常に高速の IntelliSense、コード スニペット、ソース管理の統合、および統合ターミナルを。 これは設計されていますを考慮して、データ プラットフォームのユーザーとでクエリの結果セットとカスタマイズ可能なダッシュ ボードのグラフ作成で構築されました。

調査によれば、ユーザーに費やす桁違い処理 SQL Server Management Studio で、他のタスクよりもクエリの編集に多くの時間。 そのため、Azure Data Studio は製品には、省略可能な拡張機能として利用できるその他のエクスペリエンスでは、最も使用される機能に深く集中に設計されています。 これにより、すべてのユーザーに最も頻繁に使用するワークフローをその環境をカスタマイズできます。


## <a name="how-much-does-azure-data-studio-cost"></a>Azure Data Studio のコストはどれくらいか。

Azure Data Studio は、プライベートまたは商用の使用の無料です。

## <a name="who-should-use-azure-data-studio"></a>Azure データの Studio を使用している必要があります。

Azure Data Studio だれでも使用できます。 ただし、データベース開発者、データベース管理者、システム管理者、および独立系ソフトウェア ベンダーによって実行されるタスクを簡略化するために設計されています。

## <a name="what-can-i-do-with-azure-data-studio"></a>Azure Data Studio では、どうすればでしょうか。

Data Studio の azure は、Visual Studio Code の上に構築されており、軽量、SQL Server、Azure SQL Database、Azure SQL DW を使用する場合、キーボードのフォーカスを最新のコード ワークフロー エクスペリエンス。 Azure のデータ Studio では、コア エクスペリエンスには、毎日複数タブのウィンドウ、豊富な SQL エディター、IntelliSense、キーワード補完、コード スニペットとコード ナビゲーションおよびソース管理の統合 (Git などの組み込みの機能を簡単に依存します。TFS) で変更します。 オンデマンド クエリを実行、表示 & テキスト、JSON、または Excel として結果を保存、データを編集、整理 &、お気に入りのデータベース接続を管理でき、使い慣れたオブジェクト ブラウジング操作でデータベース オブジェクトを参照できます。

お気に入りのコマンド ライン ツールを使用して (たとえば、Bash、PowerShell、sqlcmd、bcp、psql、ssh で接続)、Azure Data Studio ユーザー インターフェイス内で直接統合ターミナル ウィンドウでします。 簡単に生成し、作成を実行し、開発またはテスト目的でデータベースのコピーを作成するデータベース オブジェクトのスクリプトを挿入します。 スマートなコード スニペットと豊富なグラフィカルなエクスペリエンスを新しいデータベースとデータベース オブジェクト (テーブル、ビュー、ストアド プロシージャ、ユーザー、ログイン、ロールなど) などを作成または既存のデータベース オブジェクトを更新すると、生産性が向上します。 使用して豊富なカスタマイズ可能なダッシュ ボードを監視し、オンプレミスのデータベースで、Azure または任意のクラウドでのパフォーマンスのボトルネックを迅速にトラブルシューティングします。

Azure Data Studio は、バックアップし、復元、データベースを一貫したエクスペリエンスを提供します。 SQL Server Always-On 可用性グループの計画的なサポートにより、することが簡単に構成、監視、および、障害発生時にミッション クリティカルな SQL Server データベースと迅速にセカンダリ データベースへのフェールオーバーの Ag のトラブルシューティングを行います。 Azure Data Studio は、任意のオペレーティング システムで任意のデータベースの開発運用ライフ サイクルで生産性を向上させる設計されています。 結果としてを常にコントロール、およびリスクを減らすより速く、問題を解決および継続的に顧客の期待を超える値を提供します。

## <a name="is-azure-data-studio-open-source"></a>Azure Data Studio のオープン ソースのですか。

Azure Data Studio とそのデータ プロバイダーのソース コードは GitHub で入手できます。 (これは、Visual Studio Code に基づきます) フロント エンドの Azure Data Studio のソース コードは、ソース コードを変更し、ソフトウェアの使用がない再配布、または権利をクラウド サービスでホストを提供する使用許諾契約書で使用可能なです。 データ プロバイダーのソース コードについては、[https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice) から MIT ライセンスの下でご利用いただけます。

## <a name="do-we-plan-to-open-source-ssms"></a>オープン ソース SSMS 予定ですか。

No. ただし、次世代の複数 os と GUI の CLI ツールはオープン ソースです。 たとえば、VS Code、mssql スクリプト作成者および msql CLI mssql 拡張機能は、GitHub 上のすべてのオープン ソースです。 Azure Data Studio のソース コードは GitHub で入手できます。  

## <a name="now-that-there-is-azure-data-studio-does-microsoft-plan-to-deprecate-ssms-and-ssdt"></a>Azure Data Studio は、これでは Microsoft 廃止を計画する SSMS と SSDT のでしょうか。 

No. に加えて、次世代の複数 os と複数のデータベースと GUI の CLI ツールの主要な Windows ツール (SSMS、SSDT、PowerShell など) への投資を続けます。 目的の任意のプラットフォームで必要なツールを使用して自分のシナリオの選択肢をお客様に提供することです。 Azure Data Studio がより緊密にクエリの編集に関するエクスペリエンスに重点を置いて、どの調査によれば、データの開発は桁違いによって SQL Server Management Studio で最も頻繁に使用される機能です。 バックアップ、復元、エージェント ジョブの管理、およびサーバーのプロファイルなどの追加の価値の高い管理機能では、Azure Data Studio の拡張機能として入手できます。 Azure データ Studio もクロス プラットフォーム、任意のプラットフォームで作業できるようにします。 ただし、SQL Server Management Studio は引き続き広範な管理機能を提供し、プラットフォームの管理タスクの主要なツールのまま。 

## <a name="when-should-i-use-azure-data-studio-vs-sql-server-management-studio"></a>ときに SQL Server Management Studio の Azure データ Studio を使用して vs すればよいですか?

*場合は、Azure Data Studio を使用します。*

- ほとんどの編集、またはクエリの実行時間を費やしてください。
- すばやくグラフし、結果セットを視覚化する機能を必要があります。
- Sqlcmd または Powershell を使用して、統合ターミナルを使用して、ほとんどの管理タスクを実行できます。
- ウィザードのエクスペリエンスを最小限に抑える必要があります。
- Deep 管理またはプラットフォームに関連する構成を行う必要はありません。
- MacOS または Linux で実行する必要があります。

*場合は、SQL Server Management Studio を使用します。*

- データベース管理タスクには、ほとんどの時間を費やしてください。
- 複雑な管理やプラットフォームの構成を行っています。
- ユーザー管理、脆弱性評価、セキュリティ機能の構成など、セキュリティの管理を行っています。
- 作成する必要がありますのパフォーマンス チューニング アドバイザーとダッシュ ボードを使用します。
- データベース ダイアグラムおよびテーブル デザイナーを使用します。
- Dacpac のインポート/エクスポートを行います。
- 登録済みサーバーへのアクセスを必要があります。
- Sqlcmd モードを使用して、ライブ クエリ統計、クライアント統計を作成します。

## <a name="feature-comparison"></a>機能の比較

### <a name="shell-features"></a>シェルの機能

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|Azure サインイン|はい|はい|
|ダッシュボード|はい| |
|拡張機能|はい| |
|統合ターミナル|はい||
|オブジェクト エクスプローラー|はい|はい|
|オブジェクト スクリプト作成|はい|はい|
|プロジェクト システム|はい||
|テーブルから選択します|はい|はい|
|ソース コード管理|はい||
|作業ウィンドウ|はい||
|テーマ|はい||
|ダーク モード|はい||
|Azure リソース エクスプ ローラー|[プレビュー]||
|スクリプト生成ウィザード||はい
|Import\Export DACPAC||はい|
|オブジェクトのプロパティ||はい|
|テーブル デザイナー (Table Designer)||はい|

### <a name="query-editor"></a>クエリ エディター

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|グラフ ビューアー|はい||
|CSV、JSON、XLSX に結果をエクスポートします。|はい||
|IntelliSense|はい|はい|
|スニペット|はい|はい|
|プランを表示します。|[プレビュー]|はい|
|クライアント統計||はい|
|ライブ クエリ統計||はい|
|[クエリ オプション]||はい|
|[結果をファイルに出力]||はい|
|[結果をテキストで表示]||はい|
|空間ビューアー||はい|
|sqlcmd||[はい]|
|T-SQL デバッガー||はい|

### <a name="operating-system-support"></a>オペレーティング システムのサポート

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|Windows|はい|はい|
|macOS|はい||
|Linux|はい||

### <a name="data-engineering"></a>データ エンジニア リング

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|外部データ ウィザード|[プレビュー]||
|HDFS の統合|[プレビュー]||
|ノートブック|[プレビュー]||

### <a name="database-administration"></a>データベースの管理

|機能|Azure Data Studio|SSMS|
|:---|:---|:---|
|バックアップ/復元|はい|はい|
|フラット ファイルのインポート|[プレビュー]|はい|
|SQL エージェント|[プレビュー]|はい|
|SQL Profiler|[プレビュー]|はい|
|Always On||はい|
|Always Encrypted||はい|
|データのコピー ウィザード||はい|
|チューニング アドバイザーのデータ||[はい]|
|データベース ダイアグラム||はい|
|エラー ログの表示||はい|
|メンテナンス プラン||はい|
|マルチ サーバー クエリ||はい|
|ポリシー ベースの管理||はい|
|PolyBase||はい|
|クエリ ストア||はい|
|[登録済みサーバー]||はい|
|のレプリケーション||はい|
|セキュリティの管理||はい|
|Service Broker||はい|
|SQL Mail||はい|
|テンプレート エクスプローラー||はい|
|脆弱性評価||はい|
|XEvent 管理||はい|


## <a name="azure-data-studio-is-missing-a-feature-that-is-in-ssmsssdt-will-you-add-it"></a>Azure Data Studio には、SSMS または SSDT に含まれる機能がありません。 追加されますか?

シナリオと顧客またはビジネスのニーズによって異なります。 優先順位の参考のために、[GitHub](https://github.com/microsoft/azuredatastudio/issues) で提案してください。

## <a name="i-understand-azure-data-studio-and-the-mssql-extension-for-vs-code-are-powered-by-a-new-tools-service-that-uses-smo-apis-under-the-covers-is-smo-available-on-linux-and-macos"></a>実際には、SMO Api を使用する新しいツールのサービスを Azure Data Studio と VS Code 用 mssql 拡張機能が利用を理解しました。 SMO は、Linux と macOS で使用できるでしょうか。

SMO Api はまだ Linux または macOS で使用可能な消費できる方法で。 私たちとロードマップの一部として展開する予定に Azure Data Studio 必要な .NET Core に SMO Api のサブセットを移植できます。 SQL ツールのサービスは GitHub: [ https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice)します。

## <a name="do-you-plan-to-port-the-dacfx-apis-andor-sqlpackageexe-andor-ssdt-to-linux-and-macos"></a>DACFx Api、sqlpackage.exe、Linux と macOS に SSDT を移植する予定ですか。

長期的なロードマップ上にあります。 優先順位の参考のために、[GitHub](https://github.com/microsoft/azuredatastudio/issues) で提案してください。

## <a name="will-sql-powershell-cmdlets-be-available-on-linux-and-macos"></a>SQL PowerShell コマンドレットは Linux と macOS で提供されますか。

SQL PowerShell は、現在 PowerShell ギャラリーで入手でき、Linux 上の SQL を含む任意の場所で実行されている SQL Server で作業するために Windows で使用できます。 Linux および macOS への SQL PowerShell コマンドレットの提供はロードマップに含まれます。 優先順位の参考のために、[GitHub](https://github.com/microsoft/azuredatastudio/issues) で提案してください。

## <a name="who-usually-uses-azure-data-studio"></a>Azure Data Studio を使用するユーザーは、通常でしょうか。

開発者と Dba は、Azure Data Studio のユーザーでは通常です。

## <a name="does-azure-data-studio-integrate-with-azure-sql-data-warehouse"></a>Azure Data Studio では Azure SQL Data Warehouse と統合しますか。

可能。 データ Studio の Azure SQL Data Warehouse の azure のサポートは、Azure SQL Database マネージ インスタンス、および SQL Server 2019 のビッグ データのプレビューは現在です。

## <a name="why-is-azure-data-studio-important-for-the-new-version-of-sql-server"></a>Azure Data Studio が新しいバージョンの SQL Server の重要な理由

サポートする新しいツールが必要なように SQL Server では、ビッグ データ領域には、その機能を拡張、ユース ケースです。 そのため、Azure Data Studio は今日出荷されて、新しいプレビュー エクスペリエンスを含む最初の SQL Server ビッグ データのサポートの SQL Server のツールセットおよびリモートの SQL からデータへのアクセスする新しい外部テーブルの作成ウィザードでこれまでノートブック エクスペリエンスServer、Oracle インスタンス簡単かつ高速です。
