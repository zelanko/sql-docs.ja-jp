---
title: SSMA コンソール (AccessToSQL) を実行 |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: aa1bf665-8dc0-4259-b36f-46ae67197a43
caps.latest.revision: 25
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4400ab959c61b23c3a98c817c03506631a4d61af
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="executing-the-ssma-console-accesstosql"></a>SSMA コンソール (AccessToSQL) を実行します。
Microsoft は、堅牢な一連のスクリプト ファイルのコマンドと実行および SSMA アクティビティを制御するコマンド ライン オプションを提供します。 次のセクションでは、同じを詳しく説明します。  
  
## <a name="project--script-file-commands"></a>プロジェクト スクリプト ファイルのコマンド  
プロジェクトのコマンドでは、プロジェクトの作成、開く、保存、およびプロジェクトの終了を処理します。  
  
**Command**  
  
-プロジェクトの新規作成します。 新しい SSMA プロジェクトを作成します。  
  
**[スクリプト]**  
  
-   `project-folder` プロジェクトの作成中のフォルダーを示します。  
  
-   `project-name` プロジェクトの名前を示します。 {string}  
  
-   `overwrite-if-exists`省略可能な属性は、既存のプロジェクトを上書きするかかどうかを示します。 {boolean}  
  
-   `project-type` 省略可能な属性です。  次のオプションは、プロジェクトの種類に使用されます。  
  
    -   sql-server-2005  
  
    -   sql-server-2008  
  
    -   sql-server-2012  
  
    -   sql-server-2014  
  
    -   sql-server-2016  
  
    -   sql-azure  
  
    既定値は、「sql server 2008」です。  
  
**例:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type=”<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>”  
  
/>  
```  
' 上書き-if-exists' 属性は**false**既定です。  
  
属性 'プロジェクトの種類' **sql server 2008**既定です。  
  
**Command**  
  
開かれたプロジェクト: 既存のプロジェクトを開きます。  
  
**[スクリプト]**  
  
-   `project-folder` プロジェクトの作成中のフォルダーを示します。 指定したフォルダーが存在しない場合、コマンドが失敗します。  {string}  
  
-   `project-name` プロジェクトの名前を示します。 指定されたプロジェクトが存在しない場合、コマンドが失敗します。  {string}  
  
**構文例:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
**注:** SSMA のアクセス コンソール アプリケーションは、旧バージョンとの互換性をサポートしています。 SSMA の以前のバージョンで作成されたプロジェクトを開くことができます。  
  
**Command**  
  
保存プロジェクト: 移行プロジェクトを保存します。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
閉じるプロジェクト: 移行プロジェクトを閉じます。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<close-project  
  
  if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
'If 変更' 属性は省略可能で**無視**既定です。  
  
## <a name="database-connection-script-file-commands"></a>データベース接続のスクリプト ファイルのコマンド  
データベース接続のコマンドは、データベースへの接続を支援します。  
  
**参照**コンソールで、UI の機能がサポートされていません。  
  
**Windows 認証**と**ポート**パラメーターは、SQL Azure に接続する場合は適用されません。  
  
'を作成するスクリプト ファイル' の詳細については、次を参照してください。[スクリプト ファイルの作成&#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md)です。  
  
**Command**  
  
connect-source-database  
  
-   ソース データベースへの接続を実行し、ソース データベースが、すべてのメタデータの高レベルのメタデータを読み込みます。  
  
-   ソースへの接続を確立できない場合、エラーが生成され、さらに実行を停止するコンソール アプリケーション  
  
**[スクリプト]**  
  
サーバーの定義は、サーバー接続のファイルまたはスクリプト ファイルのサーバー セクションでは、各接続に対して定義されている名前属性から取得されます。  
  
**構文例:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
ロード access: access データベース ファイルを読み込むために使用  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<load-access-database  database-file="<Access-database>"/>  
```  
または  
  
```xml  
<load-access-database>  
  
  <access-database database-file="<Access-database1>"/>  
  
  <access-database database-file="<Access-database2>"/>  
  
</load-access-database>  
```  
**Command**  
  
force-load-source/target-database  
  
-   ソースのメタデータを読み込みます。  
  
-   移行プロジェクトをオフラインで作業するために便利です。  
  
-   ソース/ターゲットへの接続を確立できない場合、エラーが生成され、さらに実行を停止するコンソール アプリケーション  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
**構文例:**  
  
```xml  
<force-load  
  
  object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
または  
  
```xml  
<force-load>  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
reconnect-source-database  
  
-   ソース データベースへの再接続がソース データベースの接続のコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
-   (Re)、ソースとの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
connect-target-database  
  
-   ターゲット SQL Server または SQL Azure データベースに接続して、メタデータではありませんが、ターゲット データベースの高レベルのメタデータを完全に読み込みます。  
  
-   ターゲットへの接続を確立できない場合は、エラーが生成され、さらに実行を停止するコンソール アプリケーション。  
  
**[スクリプト]**  
  
サーバーの定義は、サーバー接続のファイルまたはスクリプト ファイルのサーバー セクションでは、各接続に対して定義されている名前属性から取得します。  
  
**構文例:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
reconnect-target-database  
  
-   ターゲット データベースへの再接続が、接続先データベースのコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
-   (Re) ターゲットへの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>レポート、スクリプト コマンド ファイル  
レポート コマンドは、さまざまな SSMA コンソールで操作のパフォーマンスに関するレポートを生成します。  
  
**Command**  
  
generate-assessment-report  
  
-   元のデータベースに対して評価レポートを生成します。  
  
-   このコマンドを実行する前にソース データベース接続を実行しない場合、エラーが生成され、コンソール アプリケーションを終了します。  
  
-   コマンドの実行中に、ソース データベース サーバーに接続失敗した場合も、コンソール アプリケーションが終了されます。  
  
**[スクリプト]**  
  
-   `assessment-report-folder:` 評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
-   `object-name:` 評価レポートの生成 (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) の対象オブジェクトを指定します。  
  
-   `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `assessment-report-overwrite:` 既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-summary-report-to:` レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**AssessmentReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<generate-assessment-report  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  
  write-summary-report-to="<file>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  conversion-report-folder="<folder>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
または  
  
```xml  
<generate-assessment-report  
  
  conversion-report-folder="<folder>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
    <metabase-object object-name="ssma.Procedures"  
  
        object-type="category"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-script-file-commands"></a>移行スクリプト、コマンド ファイル  
移行コマンドでは、ターゲット データベース スキーマを送信元スキーマに変換し、ターゲット サーバーにデータを移行します。  
  
設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
**Command**  
  
convert-schema  
  
-   ソースからターゲット スキーマへのスキーマの変換を実行します。  
  
-   このコマンドを実行する前に、ソースまたはターゲット データベースの接続を行わないか、コマンドの実行中にソースまたはターゲットのデータベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
**[スクリプト]**  
  
-   `conversion-report-folder:` 評価レポートの格納先フォルダーを指定します。(省略可能な属性)  
  
-   `object-name:` スキーマ (持てる indivdual オブジェクト名またはグループのオブジェクト名) に変換する対象とソース オブジェクトを指定します。  
  
-   `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `conversion-report-overwrite:` 既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-summary-report-to:` レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**SchemaConversionReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<convert-schema  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  write-summary-report-to="<filepath/folder>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
または  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder>"         (optional)  
  
  conversion-report-overwrite="<true/false>"  (optional)  
  
  <metabase-object object-name="ssma.Procedures"  
  
    object-type="category"/>  
  
</convert-schema>  
```  
**Command**  
  
データの移行  
  
1.  ターゲットに、ソース データを移行します。  
  
**[スクリプト]**  
  
-   `object-name:` 移行すると見なされるソース オブジェクトを指定します (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) データ。  
  
-   `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `write-summary-report-to:` レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**DataMigrationReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true">  
  
    <metabase-object object-name="ssma.TT1"/>  
  
    <metabase-object object-name="ssma.TT2"/>  
  
    <metabase-object object-name="ssma.TT3"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
または  
  
```xml  
<migrate-data  
  
  object-name="ssma.Tables"  
  
  object-type="category"  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true"/>  
```  
**Command**  
  
リンク テーブル。 このコマンドは、対象のテーブルにソース (アクセス) テーブルをリンクします。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</link-tables>  
```  
または  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</link-tables>  
```  
**Command**  
  
テーブルのリンクを解除します。 このコマンド ターゲット テーブルのソース (アクセス) テーブルのリンクを解除します。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</unlink-tables>  
```  
または  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</unlink-tables>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>移行の準備スクリプト、コマンド ファイル  
移行の準備中のコマンドでは、ソースとターゲット データベースの間のスキーマのマッピングを開始します。  
  
**Command**  
  
マップとスキーマ: ソース データベースが、ターゲット スキーマのスキーマのマッピング。  
  
**[スクリプト]**  
  
-   `source-schema` 移行する送信元スキーマを指定します。  
  
-   `sql-server-schema` 移行させたい場所、ターゲット スキーマを指定します。  
  
**構文例:**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>管理コマンド  
管理コマンドを使うと、ソース データベースとターゲットのデータベース オブジェクトを同期します。  
  
設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
**Command**  
  
synchronize-target  
  
1.  ターゲット データベースと、対象オブジェクトを同期します。  
  
2.  ソース データベースに対しては、このコマンドを実行する場合は、エラーが発生しました。  
  
3.  このコマンドを実行する前にターゲット データベースの接続は実行されませんか、コマンドの実行中に、ターゲット データベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
**[スクリプト]**  
  
1.  `object-name:` ターゲット データベース (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) と同期するためと見なされるターゲット オブジェクトを指定します。  
  
2.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
3.  `on-error:` 同期エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   fail-script  
  
4.  `report-errors-to:` (省略可能な属性) の同期操作だけフォルダーのパスを指定すると、し、ファイル名では、エラー レポートの場所を指定**TargetSynchronizationReport.XML**を作成します。  
  
**構文例:**  
  
```xml  
<synchronize-target  
  
  object-name="ots_triggers.dbo"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
または  
  
```xml  
<synchronize-target  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"/>  
```  
または  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="ssma.dbo.TT1"/>  
  
  <metabase-object object-name="ssma.dbo.TT2"/>  
  
  <metabase-object object-name="ssma.dbo.TT3"/>  
  
</synchronize-target>  
```  
**Command**  
  
refresh-from-database  
  
-   データベースからのソース オブジェクトを更新します。  
  
-   ターゲット データベースに対してこのコマンドを実行すると、エラーが生成されます。  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
1.  `object-name:` (持てる indivdual オブジェクト名またはグループ オブジェクトの名前)、転送元データベースから更新する場合と見なされるソース オブジェクトを指定します。  
  
2.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
3.  `on-error:` 更新エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   fail-script  
  
4.  `report-errors-to:` エラー レポートの場所を指定します (省略可能な属性) の更新操作だけフォルダーのパスを指定すると、し、ファイル名で**SourceDBRefreshReport.XML**を作成します。  
  
**構文例:**  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.TT1"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
または  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.Procedures"  
  
  object-type="category"/>  
```  
または  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="ssma.TT_1"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>スクリプトの生成のスクリプト ファイルのコマンド  
コマンドにより、スクリプトの生成は、コンソールに出力をスクリプト ファイルに保存します。  
  
**Command**  
  
save-as-script  
  
オブジェクトのスクリプトと示されているファイルを保存するために使用メタベース = target、どこでおスクリプトを取得し、実行、同じ対象のデータベースに同期コマンドには、このです。  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
-   `object-name:` あるスクリプトが保存されるオブジェクトを指定します。 (そのことがある個々 のオブジェクト名またはグループ オブジェクトの名前)  
  
-   `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `metabase:` ソースがあるかどうかを指定またはメタベースを対象にします。  
  
-   `destination:` パスまたはスクリプトが保存されるファイル名が指定されていない場合、ファイル名形式 (object_name 属性値) .out でフォルダーを指定します  
  
-   `overwrite:` true の場合、上書きされます同じファイル名が存在しない場合。 値 (真/偽) 持つことができます。  
  
**構文例:**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"  
  
  destination="<file/folder>"  
  
  overwrite="<true/false>"             (optional)  
  
/>  
```  
または  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file/folder>"  
  
    <metabase-object object-name="ssma.dbo.Procedures"  
  
                     object-type="category"/>  
  
</save-as-script>  
```  
  
## <a name="next-step"></a>次の手順  
コマンド ライン オプションについては、次を参照してください。 [SSMA コンソールでのコマンド ライン オプション&#40;AccessToSQL&#41; ](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md)です。  
  
サンプル コンソール スクリプト ファイルについては、次を参照してください[SSMA コンソールのサンプル コンソール スクリプト FilesExecuting 使用&#40;AccessToSQL。&#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
次の手順は、プロジェクトの要件によって異なります。  
  
-   パスワードまたはエクスポートを指定する/パスワードのインポートを参照してください[管理パスワード&#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md)です。  
  
-   レポートの生成に、次を参照してください。[を生成するレポート&#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md)です。  
  
-   コンソールで問題をトラブルシューティングするには、次を参照してください。[トラブルシューティング&#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md)です。  
  
