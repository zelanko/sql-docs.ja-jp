---
title: "SSMA コンソール (SybaseToSQL) を実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Database Connection Commands
- Sybase Console,Manageability Commands
- Sybase Console,Migration Commands
- Sybase Console,Migration Preparation Command
- Sybase Console,Project Commands
- Sybase Console,Report Commands
- Sybase Console,Script File Commands
- Sybase Console,Script Generation Commands
ms.assetid: ea8950b7-fabc-4aa4-89f8-9573a2617d70
caps.latest.revision: "22"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a76b457d7178483d18a5a7a26d176d7e606b6fa
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="executing-the-ssma-console-sybasetosql"></a>SSMA コンソール (SybaseToSQL) を実行します。
Microsoft で堅牢な一連のスクリプト ファイルのコマンドを実行し、SSMA 動作を制御できます。 次のセクションでは、同じを詳しく説明します。  
  
## <a name="script-file-commands"></a>スクリプト ファイルのコマンド  
コンソール アプリケーションは、このセクションで、列挙型として特定の標準的なスクリプト ファイルのコマンドを使用します。  
  
## <a name="project-commands"></a>プロジェクト コマンド  
プロジェクトのコマンドでは、プロジェクトの作成、開く、保存、およびプロジェクトの終了を処理します。  
  
### <a name="create-new-project"></a>--プロジェクトの新規作成  
このコマンドでは、新しい SSMA プロジェクトを作成します。  
  
-   `project-folder`プロジェクトの作成中のフォルダーを示します。  
  
-   `project-name`プロジェクトの名前を示します。 {文字列}  
  
-   `overwrite-if-exists`省略可能な属性は、既存のプロジェクトを上書きするかどうかを示します。 {ブール}  
  
-   `project-type:`省略可能な属性です。 「Sql server 2005」プロジェクトまたは「sql server 2008」のプロジェクトまたはプロジェクトの「sql server 2012」または「sql server 2014」プロジェクトまたは"sql azure"プロジェクトには、プロジェクトの種類を示します。 既定値は「sql server 2008 日です」  
  
**構文例:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type=”<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>”  
/>  
```  
' 上書き-if-exists' 属性は**false**既定です。  
  
属性 'プロジェクトの種類' **sql server 2008**既定です。  
  
### <a name="open-project"></a>開くプロジェクト  
このコマンドは、プロジェクトを開きます。

-   `project-folder`プロジェクトの作成中のフォルダーを示します。 指定したフォルダーが存在しない場合、コマンドが失敗します。  {文字列}  
  
-   `project-name`プロジェクトの名前を示します。 指定されたプロジェクトが存在しない場合、コマンドが失敗します。  {文字列}  
  
**構文例:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA for SAP ASE コンソール アプリケーションは、旧バージョンとの互換性をサポートします。 SSMA の以前のバージョンで作成されたプロジェクトを開くには、これを使用できます。  
  
### <a name="save-project"></a>プロジェクトの保存  
このコマンドは、移行プロジェクトを保存します。  
  
**構文例:**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>閉じるプロジェクト  
このコマンドは、移行プロジェクトを閉じます。  
  
**構文例:**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
'If 変更' 属性は省略可能で**無視**既定です。  
  
## <a name="database-connection-commands"></a>データベース接続のコマンド  
データベース接続のコマンドは、データベースへの接続を支援します。  
  
> [!NOTE]  
> - **参照**コンソールで、UI の機能がサポートされていません。  
> - 'を作成するスクリプト ファイル' の詳細については、次を参照してください。[スクリプト ファイルの作成 &#40;です。SybaseToSQL &#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>接続ソース データベース  
このコマンドは、ソース データベースへの接続を実行し、ソース データベースが、すべてのメタデータの高レベルのメタデータを読み込みます。
  
ソースへの接続を確立できない場合は、エラーが生成され、さらに実行を停止するコンソール アプリケーション。
  
サーバーの定義は、サーバー接続のファイルまたはスクリプト ファイルのサーバー セクションでは、各接続に対して定義されている名前属性から取得されます。  
  
**構文例:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>強制読み込み-ソース/ターゲット-データベース  
このコマンドは、ソースのメタデータを読み込みますあり、移行プロジェクトをオフラインで作業するために役立ちます。  
  
ソース/ターゲットへの接続を確立できない場合は、エラーが生成され、さらに実行を停止するコンソール アプリケーション。  
  
このコマンドでは、コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
**構文例:**  
  
```xml  
<force-load metabase=”<source/target>” >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>再接続ソース データベース  
このコマンドは、ソース データベースへの再接続が、ソース データベースの接続のコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
(Re)、ソースとの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**構文例:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>接続先データベース  
このコマンドは、対象の SQL Server データベースに接続し、メタデータではありませんが、ターゲット データベースの高レベルのメタデータを完全に読み込みます。  
  
ターゲットへの接続を確立できない場合は、エラーが生成され、さらに実行を停止するコンソール アプリケーション。  
  
サーバーの定義は、サーバー接続のファイルまたはスクリプト ファイルのサーバー セクションでは、各接続に対して定義されている名前属性から取得されます。  
  
**構文例:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>再接続ターゲット データベース  
  
このコマンドは、ターゲット データベースへの再接続が、接続先データベースのコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
(Re) ターゲットへの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**構文例:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>レポート コマンド  
レポート コマンドは、さまざまな SSMA コンソールで操作のパフォーマンスに関するレポートを生成します。  
  
### <a name="generate-assessment-report"></a>-評価-レポートの生成  
  
このコマンドは、元のデータベースに対して評価レポートを生成します。  
  
このコマンドを実行する前にソース データベース接続を実行しない場合、エラーが生成され、コンソール アプリケーションを終了します。  
  
コマンドの実行中に、ソース データベース サーバーに接続失敗した場合も、コンソール アプリケーションが終了されます。  
  
-   `conversion-report-folder:`評価レポートを保存するフォルダーを指定します。 (省略可能な属性)  
  
-   `object-name:`(サポートの個々 のオブジェクト名またはグループのオブジェクト名) に評価レポートの生成の対象オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリを指定すると、オブジェクトの種類は"category"になります) 場合、オブジェクト名属性でと呼ばれるオブジェクトの種類を指定します。  
  
-   `conversion-report-overwrite:`既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-summary-report-to:`レポートが生成されるパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**AssessmentReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブカテゴリがあります。  
  
    -   `report-errors`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>”             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  assessment-report-folder="<folder-name>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
内の複数の  
  
```xml  
<generate-assessment-report  
  
  assessment-report-folder="<folder-name>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
<metabase-object object-name="<object-name>"  
  
        object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-commands"></a>移行コマンド  
移行コマンドでは、ターゲット データベース スキーマを送信元スキーマに変換し、対象サーバーにデータを移行します。  
  
### <a name="convert-schema"></a>変換とスキーマ  
このコマンドでは、ソースからターゲット スキーマへのスキーマの変換を実行します。  
  
このコマンドを実行する前に、ソースまたはターゲット データベースの接続を行わないか、コマンドの実行中にソースまたはターゲットのデータベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
-   `conversion-report-folder:`評価レポートを保存するフォルダーを指定します。 (省略可能な属性)  
  
-   `object-name:`スキーマ (サポートの個々 のオブジェクト名またはグループのオブジェクト名) に変換すると見なされるソース オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリを指定すると、オブジェクトの種類は"category"になります) 場合、オブジェクト名属性でと呼ばれるオブジェクトの種類を指定します。  
  
-   `conversion-report-overwrite:`既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-summary-report-to:`概要レポートが生成されるパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**SchemaConversionReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブカテゴリがあります。  
  
    -   `report-errors`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<convert-schema  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  write-summary-report-to="<file-name/folder-name>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder-name>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
内の複数の  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>データの移行  
このコマンドは、ターゲットに、ソース データを移行します。  
  
-   `object-name:`移行すると見なされるソース オブジェクトを指定します (サポートの個々 のオブジェクト名またはグループのオブジェクト名) のデータ。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性でと呼ばれるオブジェクトの種類を指定します。  
  
-   `write-summary-report-to:`レポートが生成されるパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**DataMigrationReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブカテゴリがあります。  
  
    -   `report-errors`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>">  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
内の複数の  
  
```xml  
<migrate-data  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-command"></a>移行準備コマンド  
移行の準備中のコマンドでは、ソースとターゲット データベースの間のスキーマのマッピングを開始します。  
  
> [!NOTE]  
> 設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
### <a name="map-schema"></a>マップとスキーマ  
このコマンドは、ターゲット スキーマへのソース データベースのスキーマのマッピングを提供します。  
  
-   `source-schema`移行する送信元スキーマを指定します。  
  
-   `sql-server-schema`送信元スキーマの移行先になる、ターゲット スキーマを指定します。  
  
**構文例:**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>管理コマンド  
管理コマンドを使うと、ソース データベースとターゲットのデータベース オブジェクトを同期します。  
  
> [!NOTE]  
> 設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
### <a name="synchronize-target"></a>同期ターゲット  
このコマンドは、ターゲット データベースで、対象オブジェクトを同期します。  
 
ソース データベースに対しては、このコマンドを実行する場合は、エラーが発生しました。  
  
このコマンドを実行する前にターゲット データベースの接続は実行されませんか、コマンドの実行中に、ターゲット データベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
-   `object-name:`ターゲット データベース (サポートの個々 のオブジェクト名またはグループのオブジェクト名) と同期するためと見なされるターゲット オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性でと呼ばれるオブジェクトの種類を指定します。  
  
-   `on-error:`同期エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   警告としてレポートの合計  
  
    -   レポートの各-として-警告  
  
    -   失敗するスクリプト  
  
-   `report-errors-to:`(省略可能な属性) の同期操作のエラー レポートの場所を指定します。 だけフォルダーのパスを指定すると、ファイル名で**TargetSynchronizationReport.XML**を作成します。  
  
**構文例:**  
  
```xml  
<synchronize-target  
  
object-name="<object-name>"  
  
on-error="<report-total-as-warning/  
  
report-each-as-warning/  
  
fail-script>" (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
内の複数の  
  
```xml  
<synchronize-target  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
内の複数の  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
  
### <a name="refresh-from-database"></a>データベースからの更新  
このコマンドは、データベースからのソース オブジェクトを更新します。  
  
ターゲット データベースに対してこのコマンドを実行すると、エラーが生成されます。  
  
このコマンドでは、コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
-   `object-name:`(サポートの個々 のオブジェクト名またはグループのオブジェクト名)、転送元データベースから更新する場合と見なされるソース オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `on-error:`更新エラーの警告またはエラーとして明示するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   警告としてレポートの合計  
  
    -   レポートの各-として-警告  
  
    -   失敗するスクリプト  
  
-   `report-errors-to:`更新操作 (省略可能な属性) のエラー レポートの場所を指定します。 だけフォルダーのパスを指定すると、ファイル名で**SourceDBRefreshReport.XML**を作成します。  
  
**構文例:**  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  on-error="<report-total-as-warning/  
  
             report-each-as-warning/  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
内の複数の  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
内の複数の  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>スクリプトの生成コマンド  
スクリプトの生成コマンドは、デュアルのタスクを実行します。、コンソール出力をスクリプト ファイルに保存できると T-SQL output コンソールまたは指定したパラメーターに基づくファイルに記録します。  
  
### <a name="save-as-script"></a>-スクリプトとして保存  
このコマンドを使用して、保存をファイルにオブジェクトのスクリプトでは、ときに示されているメタベース ターゲットを = です。 これは、同期コマンドする代わりに、スクリプトを取得し、対象のデータベースで同じように実行します。  
  
このコマンドでは、コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
-   `object-name:`あるスクリプトが (サポートの個々 のオブジェクト名またはグループのオブジェクト名) に保存されるオブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリを指定すると、オブジェクトの種類は"category"になります) 場合、オブジェクト名属性でと呼ばれるオブジェクトの種類を指定します。  
  
-   `metabase:`ソースがあるかどうかを指定またはメタベースを対象にします。  
  
-   `destination:`パスまたはスクリプトを保存するフォルダーを指定します。 ファイル名が指定されていない場合は、形式 (object_name 属性値) .out 内のファイル名が提供されます。
  
-   `overwrite:`True の場合、それが上書きされます同じファイル名が存在する場合。 値 (真/偽) 持つことができます。  
  
**構文例:**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  destination="<file-name/folder-name>"  
  
  overwrite="<true/false>"   (optional)  
  
/>  
```  
内の複数の  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>sql ステートメントの変換
このコマンドでは、SQL ステートメントに変換します。  
  
-   `context`スキーマ名を指定します。  
  
-   `destination`ファイルに出力を保存するかどうかを指定します。  
  
    この属性が指定されていない場合、変換された T-SQL ステートメントは、コンソールに表示されます。 (省略可能な属性)  
  
-   `conversion-report-folder`評価レポートを保存するフォルダーを指定します。 (省略可能な属性)  
  
-   `conversion-report-overwrite`既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-converted-sql-to`変換された T-SQL ステートメントを格納するファイル (または) フォルダーのパスを指定します。 組み合わせて、フォルダー パスが指定されている場合、`sql-files`属性に、各ソース ファイルが対応するターゲットの T-SQL でファイルを指定したフォルダーの下に作成します。 組み合わせて、フォルダー パスが指定されている場合、`sql`属性、変換後の T-SQL では、指定したフォルダーの下にある Result.out をという名前のファイルに書き込まれます。  
  
-   `sql`変換する Sybase sql ステートメントを指定を使用して 1 つまたは複数のステートメントを区切ることができます、「;」  
  
-   `sql-files`T-SQL コードに変換する必要のある sql ファイルのパスを指定します。  
  
-   `write-summary-report-to`概要レポートを生成するパスを指定します。 フォルダー パスが示されているだけの場合、ファイルの名前で**ConvertSQLReport.XML**を作成します。 (省略可能な属性)  
  
    概要レポートの作成では、つまり 2 つのさらにサブカテゴリがあります。  
  
    -   -エラーの報告 (="true または false"、"false"(省略可能な属性) として既定値)。  
  
    -   詳細な ("true または false"、既定値は"false"(省略可能な属性) として = =)。  
  
このコマンドでは、コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
**構文例:**  
  
```  
<convert-sql-statement  
  
       context="<database-name>.<schema-name>"  
  
        conversion-report-folder="<folder-name>"  
  
        conversion-report-overwrite="<true/false>"  
  
        write-summary-report-to="<file-name/folder-name>"   (optional)  
  
        verbose="<true/false>"   (optional)  
  
        report-errors="<true/false>"   (optional)  
  
        destination="<stdout/file>"   (optional)  
  
        write-converted-sql-to ="<file-name/folder-name>"  
  
        sql="SELECT 1 FROM DUAL;">  
  
    <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
内の複数の  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         write-summary-report-to="<file-name/folder-name>"   (optional)  
  
         verbose="<true/false>"   (optional)  
  
         report-errors="<true/false>"   (optional)  
  
         destination="<stdout/file>"   (optional)  
  
         write-converted-sql-to ="<file-name/folder-name>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
内の複数の  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-steps"></a>次の手順  
コマンド ライン オプションについては、次を参照してください。 [SSMA コンソール (AccessToSQL) でのコマンド ライン オプション](../access/command-line-options-in-ssma-console-accesstosql.md)です。  
  
サンプルのコンソールのスクリプト ファイルについては、次を参照してください[サンプル コンソール スクリプト ファイル &#40; の操作。SybaseToSQL &#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
次の手順は、プロジェクトの要件によって異なります。  
  
-   パスワードまたはエクスポートを指定する/パスワードのインポートを参照してください[パスワードの管理 &#40;です。SybaseToSQL &#41;](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   レポートの生成に、次を参照してください。[レポートの生成 &#40;です。SybaseToSQL &#41;](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   コンソールで問題をトラブルシューティングするには、次を参照してください。[トラブルシューティング &#40;です。SybaseToSQL &#41;](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
