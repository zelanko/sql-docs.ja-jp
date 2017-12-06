---
title: "スクリプト ファイル (DB2ToSQL) を作成する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ec23d188-b890-49b8-9a88-446df96269e4
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0a000d3a8530100b1bcb4d077940b432a8b207a
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="creating-script-files-db2tosql"></a>スクリプト ファイル (DB2ToSQL) を作成します。
最初の手順とスクリプト ファイルの作成には、SSMA コンソール アプリケーションを起動する前に、変数の値のファイルと、サーバー接続ファイルを作成するために必要な場合は。  
  
スクリプト ファイルを viz 3 つのセクションに分割できます。。、します。  
  
1.  **config:**コンソール アプリケーションの構成パラメーターを設定することができます。  
  
2.  **サーバー:**ソース/ターゲットのサーバー定義を設定することができます。 別のサーバー接続ファイルでこのことができます。  
  
3.  **スクリプト コマンド:** SSMA ワークフロー コマンドを実行することができます。  
  
各セクションでは後で詳しく説明します。  
  
## <a name="configuring-db2-console-settings"></a>DB2 コンソールの設定を構成します。  
コンソールのスクリプト ファイルには、スクリプトの構成が表示されます。  
  
設定されている場合は、[構成] ノードでは、任意の要素が指定された、すべてのスクリプト コマンドの適用は、グローバル設定としてつまりです。 これらの構成要素も設定できます各コマンド内でスクリプト コマンドのセクションで、ユーザーが、グローバル設定をオーバーライドする場合。  
  
ユーザー構成可能なオプションは次のとおりです。  
  
1.  **出力のウィンドウ プロバイダー:**抑制メッセージの属性が 'true'、固有のコマンドに設定されている場合、コンソールにメッセージが表示されません操作を取得します。 属性の説明のとおりです。  
  
    -   移行先: 出力をファイルまたは標準出力に出力を取得する必要があるかどうかを指定します。 これは、既定では false です。  
  
    -   ファイル名: (省略可能) ファイルのパス。  
  
    -   抑制メッセージの数: コンソールにメッセージを表示しません。 これは既定では ' false' です。  
  
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
  
2.  **データ移行の接続プロバイダー:**を指定するソース/対象サーバーは、データ移行の対象にします。  ソースの使用-最後に使用するには、データの移行に対して最後に使用するソース サーバーを使用することを示します。 同様にターゲットの使用-最後に使用された場合は、データの移行に対して最後に使用されるターゲット サーバーを使用することを示します。 ユーザーは、属性の移行元サーバーまたはターゲット サーバーを使用しても、サーバー (ソースまたはターゲット) を指定できます。  
  
    1 つだけ、またはその他の指定した属性は、つまり使用できます。  
  
    -   ソースの使用-最後に使用された ="true"(既定値) またはソース サーバー"source_servername"を =  
  
    -   ターゲットの使用-最後に使用された ="true"(既定値) またはターゲット サーバー"target_servername"を =  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <data-migration-connection   source-use-last-used="true"  
  
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
  
3.  **ユーザー入力のポップアップ:**これにより、オブジェクトがデータベースから読み込まれるときに、エラーの処理です。 ユーザーが入力のモードを提供し、エラー発生時に、ユーザーを指定するに、コンソールが行われます。  
  
    モードは次のとおりです。  
  
    -   **質問-ユーザー -** continue('yes') またはエラー ('no') にユーザーにメッセージが表示されます。  
  
    -   **エラー-**コンソールはエラーを表示、実行を停止します。  
  
    -   **続行-**コンソールは、実行が続行されます。  
  
    既定のモードは**エラー**です。  
  
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
  
4.  **プロバイダーを再接続するには:**これにより、ユーザーは、接続エラーの設定のに備えて再接続を設定します。 これは、ソースとターゲットの両方のサーバーを設定できます。  
  
    再接続のモードは次のとおりです。  
  
    -   再接続からサーバーへの最後の使用: 最後に最大 5 回までを使用するサーバーに再接続を送信するとき、接続がアクティブでない場合。  
  
    -   エラーを生成します。 接続がアクティブでない場合、エラーが発生します。  
  
    既定のモードは**エラーを生成する**です。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <reconnect-manager  on-source-reconnect="<reconnect-to-last-used-server/generate-an-error>"  
  
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
  
5.  **コンバーター上書きプロバイダー:**これにより、ユーザーがターゲットに既に存在するオブジェクトを処理するメタベースです。 実行可能なアクションは次のとおりです。  
  
    -   エラー: コンソールのエラーが表示し、実行を中止します。  
  
    -   上書き: 既存のオブジェクトの値が上書きされます。 この操作は、既定で行われます。  
  
    -   スキップ: データベースで、コンソールが既に存在するオブジェクトをスキップ  
  
    -   要求ユーザー: ユーザーに入力を求められます ('yes' または 'no')  
  
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
  
6.  **失敗した前提条件プロバイダー:**これにより、ユーザーは、コマンドを処理するために必要な前提条件を処理します。 既定では、厳格モードは 'false' です。 'True'、例外に設定されている場合、前提条件を満たす失敗の生成を取得します。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <prerequisites strict-mode="<true/false>"/>  
  
    </output-providers>  
    ```  
  
7.  **停止操作:** 、ユーザーがその後、操作を停止する場合、中間の操作中に**' Ctrl + C'**ホット キーを使用することができます。 DB2 コンソールの SSMA では、操作が完了するを待機し、コンソールの実行を終了します。  
  
    ユーザーがその後、すぐに、実行を停止する場合は**' Ctrl + C'**ホットキーは、SSMA コンソール アプリケーションの異常終了をもう一度押すことができます。  
  
8.  **進行状況プロバイダー:**各コンソール コマンドの進行状況を通知します。 これは、既定では無効です。 進行状況レポート属性が含まれています。  
  
    -   off  
  
    -   1 間隔の %  
  
    -   毎回 ~ 2%  
  
    -   すべての 5%  
  
    -   すべての 10%  
  
    -   すべての 20%  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      progress-reporting   enable="<true/false>"            (optional)  
  
                           report-messages="<true/false>"   (optional)  
  
                           report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off" (optional)/>  
  
    </output-providers>  
    ```  
    *または*  
  
    ```xml  
    <…All commands…>  
  
      <progress-reporting  
  
        enable="<true/false>"              (optional)  
  
        report-messages="<true/false>"     (optional)  
  
        report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off"     (optional)/>  
  
    </…All commands…>  
    ```  
  
9. **ロガー詳細度:**詳細レベルのログを設定します。 これは、UI にすべてのカテゴリのオプションを使用して対応します。 既定では、ログの詳細レベルには「エラー」です。  
  
    ロガー レベルのオプションは次のとおりです。  
  
    -   致命的なエラー: のみの致命的なエラー メッセージが記録されます。  
  
    -   エラー: メッセージ エラーと致命的なエラー メッセージのみが記録されます。  
  
    -   警告: デバッグおよび情報メッセージを除くすべてのレベルがログに記録されます。  
  
    -   情報: すべてのレベル点を除いてデバッグ メッセージが記録されます。  
  
    -   デバッグ: 記録されたメッセージのすべてのレベルです。  
  
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
  
10. **暗号化されたパスワードの上書き:** 'true' の場合、クリア テキスト パスワードを指定、サーバーの定義ファイルのセクションで、サーバー接続またはスクリプト ファイルでオーバーライドの場合は保護されたストレージ上に格納されている暗号化されたパスワードが存在します。 クリア テキストでパスワードが指定されていない場合は、パスワードの入力を求められます。  
  
    ここで 2 つのケースが発生します。  
  
    1.  場合オプションのオーバーライドは**false**、検索の順序にする、保護される記憶域の&gt;スクリプト ファイルの&gt;サーバー接続ファイル-&gt;をユーザーに要求します。  
  
    2.  場合オプションのオーバーライドは**true**、検索の順序になりますスクリプト ファイルの&gt;サーバー接続ファイル-&gt;をユーザーに要求します。  
  
    **例:**  
  
    ```xml  
    <output-providers>  
  
      <encrypted-password override="<true/false>"/>  
  
    </output-providers>  
    ```  
  
構成可能な選択肢です。  
  
-   **再接続の最大試行回数:**確立された接続はタイムアウトになるか、ネットワーク障害の原因を中断、する場合、サーバーが再接続する必要です。 最大まで再接続の試行が許可されている**5**後の再試行、コンソールが自動的に再接続を実行します。 自動再接続の機能には、スクリプトを再実行で、作業が軽減されます。  
  
## <a name="server-connection-parameters"></a>サーバーの接続パラメーター  
スクリプト ファイル、またはサーバーの接続ファイルには、サーバー接続パラメーターを定義することができます。 参照してください、[サーバー接続ファイル &#40;OracleToSQL&#41; を作成する](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)詳細についてはします。  
  
## <a name="script-commands"></a>スクリプト コマンド  
スクリプト ファイルには、XML 形式で移行ワークフロー コマンドのシーケンスが含まれています。 SSMA コンソール アプリケーションでは、スクリプト ファイルに表示されるコマンドの順序で移行を処理します。  
  
たとえば、DB2 データベース内の特定のテーブルの一般的なデータの移行は次の階層: スキーマ -&gt;テーブル。  
  
スクリプト ファイル内のすべてのコマンドは正常に実行しても、SSMA コンソール アプリケーションは終了し、ユーザーに、コントロールを返します。 スクリプト ファイルの内容の詳細または小さい静的変数の情報には、いずれかが含まれている、[変数値のファイルの作成 &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)または変数の値をスクリプト ファイル内の別のセクションでします。  
  
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
製品ディレクトリのサンプル コンソール スクリプト フォルダーには、変数の値のファイル、およびサーバー接続ファイル (を実行するためのさまざまなシナリオ)、3 つのスクリプト ファイルから成るテンプレートが用意されています。  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   VariableValueFileSample.xml  
  
-   ServersConnectionFileSample.xml  
  
妥当性をそこに表示されるパラメーターを変更した後は、テンプレート (ファイル) を実行できます。  
  
スクリプト コマンドの完全な一覧は含まれて[SSMA コンソール &#40;DB2ToSQL&#41; の実行](../../ssma/db2/executing-the-ssma-console-db2tosql.md)  
  
## <a name="script-file-validation"></a>スクリプト ファイルの検証  
ユーザーが、スキーマ定義ファイルに対して自分のスクリプト ファイルを簡単に検証**'O2SSConsoleScriptSchema.xsd'** 'スキーマ' フォルダー内にあります。  
  
## <a name="next-step"></a>次の手順  
コンソールの運用には、次の手順は[変数値のファイルを作成する &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)です。  
  
## <a name="see-also"></a>参照  
[変数値ファイル &#40;DB2ToSQL&#41; の作成](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
