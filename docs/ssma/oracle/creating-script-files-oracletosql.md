---
title: スクリプト ファイル (OracleToSQL) の作成 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Script File Creation, Configuring Oracle Console Settings
- Script File Creation, Non-Configurable option
- Script File Creation, Script File Validation
ms.assetid: 55e5bc68-3040-4f07-bb00-0408a17c9821
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 879aaaf33365cb7453c1047c3f9b2408edee10f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846780"
---
# <a name="creating-script-files-oracletosql"></a>スクリプト ファイルの作成 (OracleToSQL)
SSMA コンソールのアプリケーションを起動すると、スクリプト ファイルを作成する前に、変数値ファイルとサーバー接続ファイルを作成するために必要な場合、最初の手順します。  
  
スクリプト ファイルを viz 3 つのセクションに分割できますします..,:  
  
1.  **config:** ユーザーがコンソール アプリケーションの構成パラメーターを設定できるようにします。  
  
2.  **サーバー:** ソース/ターゲットのサーバー定義を設定できます。 別のサーバー接続ファイルにこのことができます。  
  
3.  **スクリプト コマンド:** SSMA ワークフロー コマンドを実行できます。  
  
各セクションは後で詳しく説明します。  
  
## <a name="configuring-oracle-console-settings"></a>Oracle コンソールの設定を構成します。  
コンソール スクリプト ファイルには、スクリプトの構成が表示されます。  
  
設定されている場合は、[構成] ノードでは、要素のいずれかが指定された、つまりグローバル設定として適用しているすべてのスクリプト コマンド。 これらの構成要素も設定できます各コマンド内でスクリプト コマンドのセクションでは、ユーザーは、グローバル設定を上書きする必要がある場合。  
  
ユーザー構成可能なオプションは次のとおりです。  
  
1.  **出力ウィンドウ プロバイダー:** 抑制メッセージの属性が 'true'、固有のコマンドに設定されている場合、コンソールにメッセージが表示されません実行を取得します。 属性の説明のとおりです。  
  
    -   移行先: 出力をファイルまたは stdout に出力を取得する必要があるかどうかを指定します。 これは、既定では false。  
  
    -   ファイル名: (省略可能) ファイルのパス。  
  
    -   抑制メッセージ: コンソールにメッセージを抑制します。 これは、既定では ' false' です。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <output-window  
  
        suppress-messages="<true/false>"   (optional)  
  
        destination="<file/stdout>"        (optional)  
  
        file-name="<file-name>"            (optional)  
  
       />  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <…All commands…>  
  
      <output-window  
  
         suppress-messages="<true/false>"   (optional)  
  
         destination="<file/stdout>"        (optional)  
  
         file-name="<file-name>"            (optional)  
  
       />  
  
    </…All commands…>  
    ```  
  
2.  **データ移行の接続プロバイダー:** を指定しますこのソース/ターゲット サーバーはデータ移行の対象にします。  ソースの使用-最後に使用するには、データの移行に対して最後に使用される移行元サーバーを使用することを示します。 同様にターゲットの使用-最後に使用された場合は、データの移行に対して最後に使用されるターゲット サーバーを使用することを示します。 ユーザーは、属性のソース サーバーまたはターゲット サーバーを使用して、サーバー (ソースまたはターゲット) を指定もできます。  
  
    1 つだけ、または指定した属性は、つまり使用できます。  
  
    -   ソースの使用-最後に使用された ="true"(既定値) またはソース サーバー ="source_servername"  
  
    -   ターゲットの使用-最後に使用された ="true"(既定値) またはターゲット サーバー ="target_servername"  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <data-migration-connection source-use-last-used="true"  
  
                                 target-server="<target-server-unique-name>"/>  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <migrate-data>  
  
      <data-migration-connection   source-server="<source-server-unique-name>"  
  
                                   target-use-last-used="true"/>  
  
    </migrate-data>  
    ```  
  
3.  **ユーザー入力のポップアップ:** これにより、オブジェクトがデータベースから読み込まれるときに、エラーの処理。 入力のモード、ユーザーとユーザーが指定するとき、エラーが発生した場合、コンソールが進行します。  
  
    モードは次のとおりです。  
  
    -   **質問-ユーザー -** continue('yes') またはエラー ('いいえ') にユーザーにメッセージが表示されます。  
  
    -   **エラー-** コンソール エラーが表示および実行を中止します。  
  
    -   **続行-** コンソールが実行を続行します。  
  
    既定のモードは**エラー**します。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <!-- Connect to target database -->  
  
    <connect-target-database server="<target-server-unique-name>">  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </connect-target-database>  
    ```  
  
4.  **プロバイダーを再接続するには:** これによりユーザーは、接続エラーの設定が何らかの再接続を設定できます。 これは、ソースとターゲットの両方のサーバーを設定できます。  
  
    再接続モードは次のとおりです。  
  
    -   再接続からサーバーへの最後の使用: 最後に、最大で 5 回を使用するサーバーに再接続するときは、接続がアクティブでない場合。  
  
    -   エラーを生成します。 接続がアクティブでない場合、エラーが生成されます。  
  
    既定のモードは**エラーを生成**します。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <reconnect-manager on-source-reconnect="<reconnect-to-last-used-server/generate-an-error>"  
  
                         on-target-reconnect="<reconnect-to-last-used-server/generate-an-error>"/>  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <!--synchronization-->  
  
    <synchronize-target>  
  
      <reconnect-manager on-target-reconnect="reconnect-to-last-used-server"/>  
  
    </synchronize-target>  
    ```  
    *または*  
  
    ```xml  
    <!--data migration-->  
  
    <migrate-data server="<target-server-unique-name>">  
  
      <reconnect-manager  
  
        on-source-reconnect="reconnect-to-last-used-server"  
  
        on-target-reconnect="generate-an-error"/>  
  
    </migrate-data>  
    ```  
  
5.  **コンバーター上書きプロバイダー:** これにより、既にターゲットに存在するオブジェクトを処理するためにユーザー メタベースです。 実行可能なアクションは次のとおりです。  
  
    -   エラー: コンソール エラーが表示および実行を中止します。  
  
    -   上書き: 既存のオブジェクトの値が上書きされます。 このアクションは、既定で行われます。  
  
    -   スキップ: コンソール、データベースに既に存在するオブジェクトをスキップします  
  
    -   要求ユーザー: ユーザーに入力を求められます ('yes '/' いいえ')  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <convert-schema object-name="<object-name>">  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </convert-schema>  
    ```  
  
6.  **失敗した前提条件のプロバイダー:** コマンドを処理するために必要な前提条件を処理するためにユーザーは、できます。 既定では、厳格モードが 'false' です。 'True'、例外に設定されている場合、前提条件を満たすエラーの生成を取得します。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <prerequisites strict-mode="<true/false>"/>  
  
    </output-providers>  
    ```  
  
7.  **停止操作:** 、ユーザーがその後、操作を停止する場合は、中間操作中に **' Ctrl + C'** ホットキーを使用することができます。 SSMA for Oracle コンソールは、操作の完了を待機し、コンソールの実行を終了します。  
  
    ユーザーは、次に、すぐに、実行を停止する必要がある場合 **' Ctrl + C'** SSMA コンソール アプリケーションを強制的に終了のホットキーをもう一度押すこともできます。  
  
8.  **プロバイダーの進行状況:** 各コンソール コマンドの進行状況を通知します。 これは既定で無効です。 進行状況レポート属性が含まれています。  
  
    -   off  
  
    -   1-すべての %  
  
    -   2-すべての %  
  
    -   すべての 5%  
  
    -   every-10%  
  
    -   すべての 20%  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <progress-reporting enable="<true/false>"            (optional)  
  
                          report-messages="<true/false>"   (optional)  
  
                          report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off" (optional)/>  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <…All commands…>  
  
      <progress-reporting  
  
        enable="<true/false>"            (optional)  
  
        report-messages="<true/false>"   (optional)  
  
        report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off"     (optional)/>  
  
    </…All commands…>  
    ```  
  
9. **ロガーの詳細度:** セット ログの詳細度のレベル。 これは、UI にすべてのカテゴリのオプションに対応します。 既定では、ログの詳細レベルは、"error"は。  
  
    ロガー レベルのオプションは次のとおりです。  
  
    -   致命的なエラー: のみの致命的なエラー メッセージが記録されます。  
  
    -   エラー: エラーと致命的なエラーのメッセージのみが記録されます。  
  
    -   警告: デバッグおよび情報メッセージを除くすべてのレベルがログに記録されます。  
  
    -   情報: すべてのレベルを除き、デバッグ メッセージが記録されます。  
  
    -   デバッグ: 記録されたメッセージのすべてのレベル。  
  
    > [!NOTE]  
    > 必須のメッセージは、任意のレベルで記録されます。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <…All commands…>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </…All commands…>  
    ```  
  
10. **暗号化されたパスワードの上書き:** 'true' の場合、クリア テキスト パスワードを指定、サーバー接続ファイルのサーバー定義のセクションで、またはスクリプト ファイルに上書きの場合は保護されたストレージ上に格納されている暗号化されたパスワードが存在します。 クリア テキストでパスワードが指定されていない場合は、パスワードの入力を求められます。  
  
    ここでは 2 つのケースが生じます。  
  
    1.  場合オプションをオーバーライドは**false**、検索の順序になる保護されたストレージ -&gt;スクリプト ファイル -&gt;サーバー接続ファイル-&gt;をユーザーに要求します。  
  
    2.  場合上書きオプションは**true**、検索の順序になりますスクリプト ファイル -&gt;サーバー接続ファイルの&gt;をユーザーに要求します。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <encrypted-password override="<true/false>"/>  
  
    </output-providers>  
    ```  
  
構成可能なオプションです。  
  
-   **再接続の最大試行回数:** 確立された接続がタイムアウトになるか、ネットワーク障害の原因の中断する場合、サーバーが再接続する必要です。 再接続の試行が最大に許可されている**5**その後、再試行、コンソールが自動的に再接続を実行します。 自動再接続の機能で、スクリプトを再実行する作業が軽減されます。  
  
## <a name="server-connection-parameters"></a>サーバーの接続パラメーター  
スクリプト ファイル、またはサーバーの接続ファイルには、サーバーの接続パラメーターを定義できます。 参照してください、[サーバー接続ファイルを作成する&#40;OracleToSQL&#41; ](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)詳細セクション。  
  
## <a name="script-commands"></a>スクリプト コマンド  
スクリプト ファイルには、XML 形式で移行ワークフロー コマンドのシーケンスが含まれています。 SSMA コンソールのアプリケーションでは、スクリプト ファイルに表示されるコマンドの順序で移行を処理します。  
  
たとえばの階層の次の Oracle データベース内の特定のテーブルの一般的なデータ移行: スキーマ -&gt;テーブル。  
  
スクリプト ファイル内のすべてのコマンドが正常に実行された、SSMA コンソールのアプリケーションは終了し、ユーザーにコントロールを返します。 スクリプト ファイルの内容は詳細またはのいずれかに含まれる小さい静的変数の情報を[変数値ファイルの作成&#40;OracleToSQL&#41; ](../../ssma/oracle/creating-variable-value-files-oracletosql.md)または変数の値をスクリプト ファイル内の別のセクションでします。  
  
**例:**  
  
```xml  
<!--Sample of script file commands -->  
  
<ssma-script-file>  
  
  <script-commands>  
  
    <create-new-project project-folder="<project-folder>"  
  
                        project-name="<project-name>"  
  
                        overwrite-if-exists="<true/false>"/>  
  
    <connect-source-database server="<source-server-unique-name>"/>  
  
    <save-project/>  
  
    <close-project/>  
  
  </script-commands>  
  
</ssma-script-file>  
```  
製品ディレクトリのサンプルのコンソール スクリプト フォルダーには、変数値ファイル、およびサーバー接続ファイル (を実行するためのさまざまなシナリオ)、3 つのスクリプト ファイルから成るテンプレートが用意されています。  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   VariableValueFileSample.xml  
  
-   ServersConnectionFileSample.xml  
  
関連性をそこに表示されるパラメーターを変更した後、テンプレート (ファイル) を実行できます。  
  
スクリプト コマンドの完全な一覧が記載されて[SSMA コンソールの実行&#40;OracleToSQL&#41;](../../ssma/oracle/executing-the-ssma-console-oracletosql.md)  
  
## <a name="script-file-validation"></a>スクリプト ファイルの検証  
ユーザーがスキーマ定義ファイルに対してそのスクリプト ファイルを簡単に検証できます **'O2SSConsoleScriptSchema.xsd'** 'スキーマ' フォルダー内にあります。  
  
## <a name="next-step"></a>次の手順  
コンソールの運用には、次の手順は[変数値ファイルの作成&#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)します。  
  
## <a name="see-also"></a>参照  
[変数値ファイルを作成する&#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
