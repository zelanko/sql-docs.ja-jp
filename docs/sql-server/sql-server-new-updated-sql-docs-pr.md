---
title: "更新済み - SQL Server のドキュメント |Microsoft ドキュメント"
description: "更新されたコンテンツで最近変更したドキュメントについては、SQL Server 用のスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 7fba3b05943b93c0a2c0e76c2d0d5f2696a48d1c
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>新規または最近の更新: SQL Server のドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-05-01** &nbsp;対&nbsp; **2017 年-05-23**
- *サブジェクト領域:* &nbsp; **SQL Server**です。




&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2017-release-notessql-server-2017-release-notesmd"></a>1.&nbsp;[SQL Server 2017 年 1 リリース ノート](sql-server-2017-release-notes.md)

*Updated: 2017-05-17* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 28.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 84e7a2a49f2893d49380db1ad75695d9a4fd59b2 27a145ad30c10fd667f926d2e092b88c0ba586c5 -->



**SQL Server 2017 CTP 2.1 (2017 年 5 月)**

**ドキュメント (CTP 2.1)**

- **問題およびユーザーへの影響:**のドキュメントを [です。[SsSQLv14_md--.. を含める/includes/sssqlv14-md.md)] は制限されてコンテンツに含まれ、[です。[SsSQL15_md--.. を含める/includes/sssql15-md.md)] ドキュメントのセット。  固有の記事の内容 [![SsSQLv14_md--.. を含める/includes/sssqlv14-md.md)] と共に記録されます**適用先**です。 
- **問題およびユーザーへの影響:**に対するオフライン コンテンツがありません [![SsSQLv14_md--.. を含める/includes/sssqlv14-md.md)] です。

**SQL Server Reporting Services (CTP 2.1)**


- **問題およびユーザーへの影響:** SQL Server Reporting Services と Power BI でレポート サーバーを同じコンピューターし、それらのいずれかのアンインストールの両方があれば、不要になったことができます、残りのレポート サーバーはレポート Server 構成マネージャーに接続します。
- **回避策**この問題を回避するには、サーバーのいずれかをアンインストールした後に、次の操作を行う必要があります。

    1. 管理者モードでコマンド プロンプトを起動します。
    2. 残りのレポート サーバーがインストールされているディレクトリに移動します。

        *Power BI のレポート サーバーの既定の場所: C:\Program files \microsoft Power BI のレポート サーバー*

        *SQL Server Reporting Services の既定の場所: C:\Program files \microsoft SQL Server Reporting Services*

    3. 次のフォルダーに移動し、します。 これになります*SSRS*または*PBIRS*残っている新機能によって異なります。
    4. WMI フォルダーに移動します。
    5. 次のコマンドを実行します。

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        表示する場合は、次のエラーを無視できます。

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

**TSqlLanguageService.msi (CTP 2.1)**


- **問題およびユーザーへの影響:**の 2016年バージョンがあるコンピューターにインストールした後*TSqlLanguageService.msi* v13.* (SQL 2016) のバージョンのいずれか SQL セットアップで (スタンドアロン再頒布可能パッケージとして) をインストール*Microsoft.SqlServer.Management.SqlParser.dll*と*Microsoft.SqlServer.Management.SystemMetadataProvider.dll*が削除されます。 これらのアセンブリの 2016 バージョンに依存しているすべてのアプリケーションは、機能しなくのようなエラーを提供:*エラー: ファイルまたはアセンブリを読み込めませんでした ' Microsoft.SqlServer.Management.SqlParser, Version 13.0.0.0、カルチャを = = neutral, PublicKeyToken = 89845dcd8080cc91' またはその依存関係の 1 つです。システムでは、指定されたファイルを見つけることができません。*




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-what39s-new-in-sql-server-2017what-s-new-in-sql-server-2017md"></a>2.&nbsp;[何 &#39; の SQL Server 2017](what-s-new-in-sql-server-2017.md)

*Updated: 2017-05-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 31.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b3e965f62414af06d42f88497958a4bca67befce 82ad09ae9a917f26db3e2210b5cf89585e0e4c4e -->



**SQL Server 2017 CTP 2.1 (2017 年 5 月) の新機能**

* * SQL Server データベース エンジン * *

- 新しい DMF [sys.dm_db_log_stats--../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)、概要レベルの属性とトランザクション ログ ファイルに関する情報を公開するが導入されましたトランザクション ログの正常性を監視するために便利です。  
- この CTP には、バグ修正とパフォーマンスの向上、データベース エンジンが含まれています。
- 2017 年の詳細な一覧については以前の CTP リリースの CTP の機能強化は、[SQL Server 2017 (データベース エンジン)--新規は '..' を参照してください。/database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md)。

**SQL Server Reporting Services (SSRS)**

- SQL Server Reporting Services では、CTP 2.1 の時点での SQL Server のセットアップでインストールできるように不要になったです。
- コメントは、レポートに使用できるようになりました。 コメントでは、レポート内に何がパースペクティブを追加し、組織内の他のユーザーと共同作業を行うことができます。 コメントに、添付ファイルを含めることもできます。
- さらに詳細な SSRS の新機能の詳細の以前のリリースから、新しい情報、新機能 [Reporting Services--.. を参照してください。/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)。 
- Power BI のレポート サーバーについては、次を参照してください。 [Power BI のレポート サーバーの概要](https://powerbi.microsoft.com/documentation/reportserver-get-started/)です。

**SQL Server コンピューターのサービスの学習**

- この CTP では、Machine Learning のサービスの新機能はありません。
- さらに詳細な Machine Learning のサービスの新機能以前の Ctp からの詳細を含む、新しい情報、[新規の SQL Server マシン ラーニング サービス--は '..' を参照してください。/advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)。  

**SQL Server Analysis Services (SSAS)**

- この CTP に新しい SSAS 機能はありません。  
- 機能強化とバグ修正を行いました。 このリリースの詳細については、[新規で SQL Server 2017 Analysis Services - は '..' を参照してください。/analysis-services/what-s-new-in-sql-server-analysis-services-2017.md)。  





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この圧縮リストは、前のセクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [SQL Server 2017 年 1 リリース ノートします。](#TitleNum_1)
2. [どのような &#39; の SQL Server 2017](#TitleNum_2)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>関連記事

このセクションには、同じの GitHub リポジトリ内の他のサブジェクト領域の最近更新されたアーティクルのアーティクルを非常に似ていますが一覧表示します。


&nbsp;

[Microsoft/**sql docs-pr** ](https://github.com/microsoftdocs/sql-docs-pr/) GitHub.com 上のリポジトリ。

- [最近更新された:**リレーショナル データベースおよび Microsoft SQL Server** docs](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [最近更新された: **Microsoft SQL Server** docs](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [最近更新された: **SQL server TRANSACT-SQL** docs](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



