---
title: "SSMA コンソール (OracleToSQL) を実行 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Oracle SSMA Console
- Script File Commands, Script Generation Commands,Manageability Commands
- Script File Commands,Project Commands
ms.assetid: 7228ccba-c69f-4b4c-8664-01a2750183c5
caps.latest.revision: 43
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 685286966599c4dcd3dc2f7029413c77f3ff2689
ms.openlocfilehash: 4ca3c3557b7f57b93dc41b23232754c5df046bdb
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="executing-the-ssma-console-oracletosql"></a>SSMA コンソール (OracleToSQL) を実行します。
Microsoft で堅牢な一連のスクリプト ファイルのコマンドを実行し、SSMA 動作を制御できます。 コンソール アプリケーションは、このセクションで、列挙型として特定の標準的なスクリプト ファイルのコマンドを使用します。  
  
## <a name="project-script-file-commands"></a>プロジェクト スクリプト ファイルのコマンド  
プロジェクトのコマンドでは、プロジェクトの作成、開く、保存、およびプロジェクトの終了を処理します。  
  
**Command**  
  
--プロジェクトの新規作成  
                  : 新しい SSMA プロジェクトを作成します。  
  
**[スクリプト]**  
  
-   `project-folder`プロジェクトの作成中のフォルダーを示します。  
  
-   `project-name`プロジェクトの名前を示します。 {文字列}  
  
-   `overwrite-if-exists`省略可能な属性は、既存のプロジェクトを上書きするかかどうかを示します。 {ブール}  
  
-   `project-type:`省略可能な属性です。 プロジェクトの種類「sql server 2005」プロジェクトつまりまたは「sql server 2008」のプロジェクトまたはプロジェクトの「sql server 2012」または「sql server 2014」プロジェクトまたは"sql azure"を示します。 既定値は、「sql server 2014」です。  
  
**例:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014>"   (optional)  
  
/>  
```  
' 上書き-if-exists' 属性は**false**既定です。  
  
属性 'プロジェクトの種類' **sql server 2008**既定です。  
  
**Command**  
  
開かれたプロジェクト: 既存のプロジェクトを開きます。  
  
**[スクリプト]**  
  
-   `project-folder`プロジェクトの作成中のフォルダーを示します。 指定したフォルダーが存在しない場合、コマンドが失敗します。  {文字列}  
  
-   `project-name`プロジェクトの名前を示します。 指定されたプロジェクトが存在しない場合、コマンドが失敗します。  {文字列}  
  
**構文例:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
Oracle のコンソール アプリケーションの SSMA では、旧バージョンとの互換性をサポートします。 SSMA の以前のバージョンで作成されたプロジェクトを開くことができます。  
  
**Command**  
  
プロジェクトの保存  
  
移行プロジェクトを保存します。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
閉じるプロジェクト  
  
移行プロジェクトを閉じます。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
  
## <a name="database-connection-script-file-commands"></a>データベース接続のスクリプト ファイルのコマンド  
データベース接続のコマンドは、データベースへの接続を支援します。  
  
-   **参照**コンソールで、UI の機能がサポートされていません。  
  
-   'を作成するスクリプト ファイル' の詳細については、次を参照してください。[スクリプト ファイルの作成 &#40;OracleToSQL"&"#41;](../../ssma/oracle/creating-script-files-oracletosql.md)です。  
  
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
<force-load object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
または  
  
```xml  
<force-load>  
  
   <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
再接続ソース データベース  
  
-   ソース データベースへの再接続がソース データベースの接続のコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
-   (Re)、ソースとの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
接続先データベース  
  
-   対象の SQL Server データベースに接続して、メタデータではありませんが、ターゲット データベースの高レベルのメタデータを完全に読み込みます。  
  
-   ターゲットへの接続を確立できない場合は、エラーが生成され、さらに実行を停止するコンソール アプリケーション。  
  
**[スクリプト]**  
  
サーバーの定義は、サーバー接続のファイルまたはスクリプト ファイルのサーバー セクションでは、各接続に対して定義されている名前属性から取得します。  
  
**構文例:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
再接続ターゲット データベース  
  
-   ターゲット データベースへの再接続が、接続先データベースのコマンドとは異なり、すべてのメタデータが読み込まれない。  
  
-   (Re) ターゲットへの接続を確立できない場合、エラーが発生し、さらに実行を停止するコンソール アプリケーションです。  
  
**[スクリプト]**  
  
**構文例:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file--commands"></a>レポート、スクリプト コマンド ファイル  
レポート コマンドは、さまざまな SSMA コンソールで操作のパフォーマンスに関するレポートを生成します。  
  
**Command**  
  
-評価-レポートの生成  
  
-   元のデータベースに対して評価レポートを生成します。  
  
-   このコマンドを実行する前にソース データベース接続を実行しない場合、エラーが生成され、コンソール アプリケーションを終了します。  
  
-   コマンドの実行中に、ソース データベース サーバーに接続失敗した場合も、コンソール アプリケーションが終了されます。  
  
**[スクリプト]**  
  
-   `conversion-report-folder:`評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
-   `object-name:`評価レポートの生成 (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) の対象オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `conversion-report-overwrite:`既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-summary-report-to:`概要レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**AssessmentReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   assessment-report-folder="<folder-name>"   (optional)  
  
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
  
## <a name="migration-script-file-commands"></a>移行スクリプト、コマンド ファイル  
移行コマンドでは、ターゲット データベース スキーマを送信元スキーマに変換し、ターゲット サーバーにデータを移行します。  
  
設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
**Command**  
  
変換とスキーマ  
  
-   ソースからターゲット スキーマへのスキーマの変換を実行します。  
  
-   このコマンドを実行する前に、ソースまたはターゲット データベースの接続を行わないか、コマンドの実行中にソースまたはターゲットのデータベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
**[スクリプト]**  
  
-   `conversion-report-folder:`評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
-   `object-name:`スキーマ (持てる indivdual オブジェクト名またはグループのオブジェクト名) に変換する対象とソース オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `conversion-report-overwrite:`既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-summary-report-to:`概要レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**SchemaConversionReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
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
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
データの移行  
  
ターゲットに、ソース データを移行します。  
  
**[スクリプト]**  
  
-   `conversion-report-folder:`評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
-   `object-name:`移行すると見なされるソース オブジェクトを指定します (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) データ。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `conversion-report-overwrite:`既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-summary-report-to:`概要レポートを生成するパスを指定します。  
  
    フォルダー パスが示されているだけの場合、ファイルの名前で**DataMigrationReport&lt;n&gt;です。XML**を作成します。 (省略可能な属性)  
  
    レポートの作成には、さらに 2 つのサブ カテゴリがあります。  
  
    -   `report-errors`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
    -   `verbose`("true または false"、既定値は"false"(省略可能な属性) として = =)  
  
**構文例:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>">  
  
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
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>移行の準備スクリプト、コマンド ファイル  
移行の準備中のコマンドでは、ソースとターゲット データベースの間のスキーマのマッピングを開始します。  
  
**Command**  
  
マップとスキーマ  
  
ターゲット スキーマへのソース データベースのスキーマ マッピングです。  
  
ターゲットに、ソース データを移行します。  
  
**[スクリプト]**  
  
-   `source-schema`移行する送信元スキーマを指定します。  
  
-   `sql-server-schema`移行させたい場所、ターゲット スキーマを指定します。  
  
**構文例:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>管理の容易性、スクリプト コマンド ファイル  
管理コマンドを使うと、ソース データベースとターゲットのデータベース オブジェクトを同期します。 設定の移行コマンドの既定のコンソール出力は、詳細なエラー レポートを作成しないとレポートを 'Full' の出力: ソース オブジェクト ツリーのルート ノードで概要のみです。  
  
**Command**  
  
同期ターゲット  
  
-   ターゲット データベースと、対象オブジェクトを同期します。  
  
-   ソース データベースに対しては、このコマンドを実行する場合は、エラーが発生しました。  
  
-   このコマンドを実行する前にターゲット データベースの接続は実行されませんか、コマンドの実行中に、ターゲット データベース サーバーへの接続が失敗する場合、エラーが生成され、コンソール アプリケーションの終了します。  
  
**[スクリプト]**  
  
-   `object-name:`ターゲット データベース (持てる indivdual オブジェクト名またはグループ オブジェクトの名前) と同期するためと見なされるターゲット オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `on-error:`同期エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   警告としてレポートの合計  
  
    -   レポートの各-として-警告  
  
    -   失敗するスクリプト  
  
-   `report-errors-to:`(省略可能な属性) の同期操作だけフォルダーのパスを指定すると、し、ファイル名では、エラー レポートの場所を指定**TargetSynchronizationReport.XML**を作成します。  
  
**構文例:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
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
  
-   データベースからのソース オブジェクトを更新します。  
  
-   ターゲット データベースに対してこのコマンドを実行すると、エラーが生成されます。  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
-   `object-name:`(そのことがある個々 のオブジェクト名またはグループ オブジェクトの名前)、転送元データベースから更新する場合と見なされるソース オブジェクトを指定します。  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `on-error:`更新エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
    -   警告としてレポートの合計  
  
    -   レポートの各-として-警告  
  
    -   失敗するスクリプト  
  
-   `report-errors-to:`エラー レポートの場所を指定します (省略可能な属性) の更新操作だけフォルダーのパスを指定すると、し、ファイル名で**SourceDBRefreshReport.XML**を作成します。  
  
**構文例:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
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
  
-スクリプトとして保存  
  
オブジェクトのスクリプトと示されているファイルを保存するために使用メタベース = target、どこでおスクリプトを取得し、実行、同じ対象のデータベースに同期コマンドには、このです。  
  
**[スクリプト]**  
  
コマンド ライン パラメーターとして 1 つまたはいくつかのメタベース ノードが必要です。  
  
-   `object-name:`あるスクリプトが保存されるオブジェクトを指定します。 (そのことがある個々 のオブジェクト名またはグループ オブジェクトの名前)  
  
-   `object-type:`(オブジェクトのカテゴリが指定した場合、オブジェクトの種類は"category")、オブジェクト名属性で指定されたオブジェクトの種類を指定します。  
  
-   `metabase:`指定するかどうか、このソースか、メタベースを対象します。  
  
-   `destination:`パスまたはスクリプトが保存されるファイル名が指定されていない場合、ファイル名形式 (object_name 属性値) .out でフォルダーを指定します  
  
-   `overwrite:`true の場合、上書きされます同じファイル名が存在しない場合。 値 (真/偽) 持つことができます。  
  
**構文例:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file/folder>"  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
または  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file/folder>"  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
sql ステートメントの変換  
  
-   `context`スキーマ名を指定します。  
  
-   `destination`ファイルに出力を保存するかどうかを指定します。  
  
    この属性が指定されていない場合、変換された T-SQL ステートメントは、コンソールに表示されます。 (省略可能な属性)  
  
-   `conversion-report-folder`評価レポートを格納することができます、フォルダーを指定します。(省略可能な属性)  
  
-   `conversion-report-overwrite`既に存在する場合は、評価レポート フォルダーを上書きするかどうかを指定します。  
  
    **既定値:** false を指定します。 (省略可能な属性)  
  
-   `write-converted-sql-to`ファイル (または)、変換された T-SQL が格納されるフォルダーのパスを指定します。 組み合わせて、フォルダー パスが指定されている場合、`sql-files`属性に、各ソース ファイルが対応するターゲットの T-SQL でファイルを指定したフォルダーの下に作成します。 組み合わせて、フォルダー パスが指定されている場合、`sql`属性に、変換後の T-SQL はという名前のファイルに書き込まれます。 **Result.out**指定したフォルダーの下。  
  
-   `sql`変換する、1 つまたは複数のステートメントに Oracle sql ステートメントを指定できる区切りを使用する、「;」  
  
-   `sql-files`T-SQL コードに変換する必要がある sql ファイルのパスを指定します。  
  
-   `write-summary-report-to`レポートを生成するパスを指定します。 フォルダー パスが示されているだけの場合、ファイルの名前で**ConvertSQLReport.XML**を作成します。 (省略可能な属性)  
  
    レポートの作成が viz サブカテゴリの一覧をさらに 2 です。 します。  
  
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
  
   destination="<stdout/file>"   (optional)  
  
   file-name="<file-name>"  
  
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
  
   write-summary-report-to="<file-name/folder-name>" (optional)  
  
   verbose="<true/false>" (optional)  
  
   report-errors="<true/false>"  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
または  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
  
## <a name="next-step"></a>次の手順  
コマンド ライン オプションについては、次を参照してください。 [SSMA コンソール &#40;OracleToSQL"&"#41; でのコマンド ライン オプション](../../ssma/oracle/command-line-options-in-ssma-console-oracletosql.md)です。  
  
サンプル コンソール スクリプト ファイルについては、次を参照してください[サンプル コンソール スクリプト ファイル &#40;OracleToSQL"&"#41; の操作。](../../ssma/oracle/working-with-the-sample-console-script-files-oracletosql.md)  
  
次の手順は、プロジェクトの要件によって異なります。  
  
-   パスワードまたはエクスポートを指定する/パスワードのインポートを参照してください[パスワードを管理する &#40;OracleToSQL"&"#41;](../../ssma/oracle/managing-passwords-oracletosql.md)です。  
  
-   レポートの生成に、次を参照してください。[レポートを生成する &#40;OracleToSQL"&"#41;](../../ssma/oracle/generating-reports-oracletosql.md)です。  
  
-   コンソールで問題をトラブルシューティングするには、次を参照してください。[トラブルシューティング &#40;OracleToSQL"&"#41;](../../ssma/oracle/troubleshooting-oracletosql.md)です。  
  

