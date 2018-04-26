---
title: SSMA コンソール (MySQLToSQL) を実行 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
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
helpviewer_keywords:
- Script file commands, Database connection commands
- Script file commands, Manageability commands
- Script file commands, Migration commands
- Script file commands, Migration preparation commands
- Script file commands, project commands
- Script file commands, Report commands
- Script file commands, Script generation commands
ms.assetid: e3e9f7e4-0619-4861-a202-3d5d39953b26
caps.latest.revision: 25
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b8946a6abdce48e55624965d1dea8b17c40760ea
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="executing-the-ssma-console-mysqltosql"></a>SSMA コンソール (MySQLToSQL) を実行します。
Microsoft で堅牢な一連のスクリプト ファイルのコマンドを実行し、SSMA 動作を制御できます。  
  
コンソール アプリケーションは、このセクションで、列挙型として特定の標準的なスクリプト ファイルのコマンドを使用します。  
  
## <a name="project--script-file-commands"></a>プロジェクト スクリプト ファイルのコマンド  
**Command**  
  
create-new-project:   
                   新しい SSMA プロジェクトを作成します。  
  
プロジェクトのコマンドでは、プロジェクトの作成、開く、保存、およびプロジェクトの終了を処理します。  
  
**[スクリプト]**  
  
1.  `project-folder` プロジェクトの作成中のフォルダーを示します。  
  
2.  `project-name` プロジェクトの名前を示します。 {string}  
  
3.  `overwrite-if-exists`省略可能な属性は、既存のプロジェクトを上書きするかかどうかを示します。 {boolean}  
  
4.  `project-type:`省略可能な属性です。 プロジェクトの種類などの「sql server 2005」プロジェクトまたは「sql server 2008」のプロジェクトまたは「sql server 2012」または「sql server 2014」プロジェクトまたはプロジェクトの"sql azure"を示します。 既定値は、「sql server 2008」です。  
  
**構文例:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type==”<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>”   (optional)  
  
/>  
```  
' 上書き-if-exists' 属性は**false**既定です。  
  
属性 'プロジェクトの種類' **sql server 2008**既定です。  
  
**Command**  
  
開かれたプロジェクト。   
                  既存のプロジェクトを開きます。  
  
**[スクリプト]**  
  
1.  `project-folder` プロジェクトの作成中のフォルダーを示します。 指定したフォルダーが存在しない場合、コマンドが失敗します。  {string}  
  
2.  `project-name` プロジェクトの名前を示します。 指定されたプロジェクトが存在しない場合、コマンドが失敗します。  {string}  
  
**構文例:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
> [!IMPORTANT]  
> MySQL コンソール アプリケーションの SSMA では、旧バージョンとの互換性をサポートします。 SSMA の以前のバージョンで作成されたプロジェクトを開くことができます。  
  
**Command**  
  
保存プロジェクト: 移行プロジェクトを保存します。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
close-project  
                  : 移行プロジェクトを閉じます。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
close-project  
                  : 移行プロジェクトを閉じます。  
  
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
  
1.  **参照**コンソールで、UI の機能がサポートされていません。  
  
2.  **Windows 認証**と**ポート**パラメーターは、SQL Azure に接続する場合は適用されません。  
  
3.  'を作成するスクリプト ファイル' の詳細については、次を参照してください。[スクリプト ファイルの作成&#40;MySQLToSQL&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md)です。  
  
**Command**  
  
接続ソース データベース  
  
-   ソース データベースへの接続を実行し、ソース データベースが、すべてのメタデータの高レベルのメタデータを読み込みます。  
  
-   ソースへの接続を確立できない場合、エラーが生成され、さらに実行を停止するコンソール アプリケーション  
  
**[スクリプト]**  
  
サーバーの定義は、サーバー接続のファイルまたはスクリプト ファイルのサーバー セクションでは、各接続に対して定義されている名前属性から取得されます。  
  
**構文例:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
強制読み込み-ソース/ターゲット-データベース  
  
-   ソースのメタデータを読み込みます。  
  
-   移行プロジェクトをオフラインで作業するために便利です。  
  
-   ソース/ターゲットへの接続を確立できない場合、エラーが生成され、さらに実行を停止するコンソール アプリケーション  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
**構文例:**  
  
```xml  
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
再接続ソース データベース  
  
1.  ソース データベースへの再接続がソース データベースの接続のコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
2.  (Re)、ソースとの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
connect-target-database  
  
1.  ターゲット SQL Server または SQL Azure データベースに接続して、メタデータではありませんが、ターゲット データベースの高レベルのメタデータを完全に読み込みます。  
  
2.  ターゲットへの接続を確立できない場合は、エラーが生成され、さらに実行を停止するコンソール アプリケーション。  
  
**[スクリプト]**  
  
サーバーの定義は、サーバー接続のファイルまたはスクリプト ファイルのサーバー セクションでは、各接続に対して定義されている名前属性から取得します。  
  
**構文例:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
reconnect-target-database  
  
1.  ターゲット データベースへの再接続が、接続先データベースのコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
2.  (Re) ターゲットへの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>レポート、スクリプト コマンド ファイル  
レポート コマンドは、さまざまな SSMA コンソールで操作のパフォーマンスに関するレポートを生成します。  
  
**Command**  
  
generate-assessment-report  
  
1.  元のデータベースに対して評価レポートを生成します。  
  
2.  このコマンドを実行する前にソース データベース接続を実行しない場合、エラーが生成され、コンソール アプリケーションを終了します。  
  
3.  コマンドの実行中に、ソース データベース サーバーに接続失敗した場合も、コンソール アプリケーションが終了されます。  
  
**[スクリプト]**  
  
1.  `assessment-report-folder:` 評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
2.  `object-name:` (そのことがある個々 のオブジェクト名またはグループ オブジェクトの名前) 評価レポートの生成の対象オブジェクトを指定します。  
  
3.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
4.  `assessment-report-overwrite:` 既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
5.  `write-summary-report-to:` 概要レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**AssessmentReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
または  
  
```xml  
<generate-assessment-report  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
>  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration--script-file-commands"></a>移行スクリプト、コマンド ファイル  
移行コマンドでは、ターゲット データベース スキーマを送信元スキーマに変換し、ターゲット サーバーにデータを移行します。  
  
設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
**Command**  
  
変換とスキーマ  
  
1.  ソースからターゲット スキーマへのスキーマの変換を実行します。  
  
2.  このコマンドを実行する前に、ソースまたはターゲット データベースの接続を行わないか、コマンドの実行中にソースまたはターゲットのデータベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
**[スクリプト]**  
  
1.  `conversion-report-folder:` 評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
2.  `object-name:` スキーマ (持てる indivdual オブジェクト名またはグループのオブジェクト名) に変換する対象のオブジェクトを指定します。  
  
3.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
4.  `conversion-report-overwrite:` 既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
5.  `write-summary-report-to:` 概要レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**SchemaConversionReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    概要レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<convert-schema  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
または  
  
```xml  
<convert-schema  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
      <metabase-object object-name="<object-names>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
データの移行  
  
1.  ターゲットに、ソース データを移行します。  
  
**[スクリプト]**  
  
1.  `object-name:` 移行すると見なされるソース オブジェクトを指定します (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) データ。  
  
2.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
3.  `write-summary-report-to:` 概要レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**DataMigrationReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose` ("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>”  
  
   report-errors="true" verbose="true">  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <data-migration-connection  
  
         source-use-last-used="true"/source-server="<server-unique-name>"  
  
         target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
または  
  
```xml  
<migrate-data  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>”  
  
   report-errors="true" verbose="true"/>  
```  
  
## <a name="migration-preparation-script-file-command"></a>移行の準備スクリプト ファイル コマンド  
移行の準備中のコマンドでは、ソースとターゲット データベースの間のスキーマのマッピングを開始します。  
  
**Command**  
  
マップとスキーマ  
  
ターゲット スキーマへのソース データベースのスキーマ マッピングです。  
  
**[スクリプト]**  
  
1.  `source-schema` 移行する送信元スキーマを指定します。  
  
2.  `sql-server-schema` 移行させたい場所、ターゲット スキーマを指定します。  
  
**構文例:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>管理の容易性、スクリプト コマンド ファイル  
管理コマンドを使うと、ソース データベースとターゲットのデータベース オブジェクトを同期します。  
  
> [!NOTE]  
> 設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
**Command**  
  
同期ターゲット  
  
1.  ターゲット データベースと、対象オブジェクトを同期します。  
  
2.  ソース データベースに対しては、このコマンドを実行する場合は、エラーが発生しました。  
  
3.  このコマンドを実行する前にターゲット データベースの接続は実行されませんか、コマンドの実行中に、ターゲット データベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
**[スクリプト]**  
  
1.  `object-name:` ターゲット データベース (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) との同期の対象オブジェクトを指定します。  
  
2.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
3.  `on-error:` 同期エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   失敗するスクリプト  
  
4.  `report-errors-to:` (省略可能な属性) の同期操作だけフォルダーのパスを指定すると、し、ファイル名では、エラー レポートの場所を指定**TargetSynchronizationReport.XML**を作成します。  
  
**構文例:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
/>  
```  
または  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
または  
  
```xml  
<synchronize-target>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
**Command**  
  
データベースからの更新  
  
1.  データベースからのソース オブジェクトを更新します。  
  
2.  ターゲット データベースに対してこのコマンドを実行すると、エラーが生成されます。  
  
**[スクリプト]**  
  
1.  `object-name:` (持てる indivdual オブジェクト名またはグループ オブジェクトの名前)、転送元データベースから更新する場合と見なされるソース オブジェクトを指定します。  
  
2.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
3.  `on-error:` 同期エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   失敗するスクリプト  
  
4.  `report-errors-to:` (省略可能な属性) の同期操作だけフォルダーのパスを指定すると、し、ファイル名では、エラー レポートの場所を指定**SourceDBRefreshReport.XML**を作成します。  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
**構文例:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
/>  
```  
または  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
または  
  
```xml  
<refresh-from-database>  
  
   <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>スクリプトの生成のスクリプト ファイルのコマンド  
スクリプトの生成コマンドは、デュアルのタスクを実行しますコンソールのスクリプト ファイルに出力を保存できる。コンソールまたは指定したパラメーターに基づいてファイルを T-SQL で出力を記録します。  
  
**Command**  
  
save-as-script  
  
オブジェクトのスクリプトと示されているファイルを保存するために使用メタベース = target、どこでおスクリプトを取得し、実行、同じ対象のデータベースに同期コマンドには、このです。  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
1.  `object-name:` あるスクリプトが保存されるオブジェクトを指定します。 (持てる indivdual オブジェクト名またはグループ オブジェクトの名前)  
  
2.  `object-type:` (オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
3.  `metabase:` ソースがあるかどうかを指定またはメタベースを対象にします。  
  
4.  `destination:` パスまたはスクリプトが保存されるファイル名が指定されていない場合、ファイル名形式 (object_name 属性値) .out でフォルダーを指定します  
  
5.  `overwrite:` true の場合、上書きされます同じファイル名が存在しない場合。 値 (真/偽) 持つことができます。  
  
**構文例:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file-name/folder-name>”  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
または  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file-name/folder-name>”  
  
      <metabase-object object-name="<object-name>"  
  
            object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
convert-sql-statement  
  
1.  `context` スキーマ名を指定します。  
  
2.  `destination` ファイルに出力を保存するかどうかを指定します。  
  
    この属性が指定されていない場合、変換された T-SQL ステートメントは、コンソールに表示されます。 (省略可能な属性)  
  
3.  `conversion-report-folder` 評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
4.  `conversion-report-overwrite` 既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
5.  `write-converted-sql-to` ファイル (または)、変換された T-SQL が格納されるフォルダーのパスを指定します。 組み合わせて、フォルダー パスが指定されている場合、`sql-files`属性に、各ソース ファイルが対応するターゲットの T-SQL でファイルを指定したフォルダーの下に作成します。 組み合わせて、フォルダー パスが指定されている場合、`sql`属性、変換後の T-SQL では、指定したフォルダーの下にある Result.out をという名前のファイルに書き込まれます。  
  
6.  `sql` 変換する、1 つまたは複数のステートメントの MySQL sql ステートメントを指定できる区切りを使用する、「;」  
  
7.  `sql-files` T-SQL コードに変換する必要がある sql ファイルのパスを指定します。  
  
8.  `write-summary-report-to` 概要レポートを生成するパスを指定します。 フォルダー パスが示されているだけの場合、ファイルの名前で**ConvertSQLReport.XML**を作成します。 (省略可能な属性)  
  
    レポートの作成が viz サブカテゴリの一覧をさらに 2します..,:  
  
    -   -エラーの報告 (="true または false"、"false"(省略可能な属性) として既定値)。  
  
    -   詳細な ("true または false"、既定値は"false"(省略可能な属性) として = =)。  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
**構文例:**  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="stdout/file"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql="SELECT 1 FROM DUAL;">  
  
      <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
または  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
または  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>次の手順  
コマンド ライン オプションについては、次を参照してください。 [SSMA コンソールでのコマンド ライン オプション&#40;MySQLToSQL&#41; ](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md)です。  
  
サンプル コンソール スクリプト ファイルの詳細については、次を参照してください[サンプル コンソール スクリプト ファイルで作業&#40;MySQLToSQL。&#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
次の手順は、プロジェクトの要件によって異なります。  
  
1.  パスワードまたはエクスポートを指定する/パスワードのインポートを参照してください[管理パスワード&#40;MySQLToSQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md)です。  
  
2.  レポートの生成に、次を参照してください。[を生成するレポート&#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md)です。  
  
3.  コンソールで問題をトラブルシューティングするには、次を参照してください。[トラブルシューティング&#40;MySQLToSQL&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md)です。  
  
