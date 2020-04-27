---
title: サンプルのコンソールスクリプトファイルの操作 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sample console script files
ms.assetid: 7e6aaa8a-5f5c-414d-9fb8-21e56b9ffaef
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6dacba33ecbaa7bdeb51d0a31438c3cbdb21969f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67904895"
---
# <a name="working-with-the-sample-console-script-files-mysqltosql"></a>サンプルのコンソールスクリプトファイルの操作 (MySQLToSQL)
ユーザー参照および使用のために、いくつかのサンプルファイルが製品と共に提供されています。 このセクションでは、エンドユーザーのニーズに合わせて、これらのスクリプトを簡単にカスタマイズする方法について説明します。  
  
## <a name="sample-console-script-files"></a>サンプルコンソールスクリプトファイル  
さまざまなシナリオをカバーする次のサンプルコンソールスクリプトファイルは、ユーザー参照用に用意されています。  
  
-   すべてのファイル  
  
-   変数の形式  
  
-   AssessmentReportGenerationSample  
  
-   SqlStatementConversionSample  
  
-   ConversionAndDataMigrationSample  
  
-   **次のようにします。**  
  
    -   このサンプルでは、ソースとターゲットのデータベースで使用できるさまざまなモードの接続を提供し、ユーザーは要件に従って任意のモードを選択できます。 このサンプルには、サーバー定義が含まれています。  
  
    -   ユーザーは、必要なソースとターゲットのサーバー定義に値を変更するだけで、必要なデータベースに接続できます。 この例では、すべての値が変数の値として指定されて**います。これは、変数**に使用できます。  その他のすべての接続パラメーターは、ユーザーの作業サーバー接続ファイルから削除できます。  
  
    -   ソースサーバーとターゲットサーバーへの接続の詳細については、「 [MySQLToSQL&#41;&#40;のサーバー接続ファイルの作成](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)」を参照してください。  
  
-   **変数 Valuefiles. .xml:** サンプルコンソールスクリプトファイルで使用されており、 `ServersConnectionFileSample.xml`このファイルで照合されているすべての変数。 サンプルのコンソールスクリプトを実行するには、ユーザーがサンプル変数の値をユーザー定義の変数に置き換えるだけで、このファイルを追加のコマンドライン引数としてスクリプトファイルと共に渡す必要があります。  
  
    変数値ファイルの詳細については、「 [MySQLToSQL&#41;&#40;の変数値ファイルの作成](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)」を参照してください。  
  
-   **AssessmentReportGenerationSample:** このサンプルを使用すると、データの変換と移行を開始する前にユーザーが分析に使用できる xml 評価レポートを生成できます。  
  
    この`generate-assessment-report`コマンドでは、ユーザーは属性の`object-name`変数値 (mandatorily を**参照)** をユーザーが使用しているデータベース名に変更する必要があります。 指定されたオブジェクトの種類によっ`object-type`ては、値も変更する必要があります。  
  
    ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルの`generate-assessment-report`コンソールスクリプトファイルの例4に示すように、複数のノードを指定できます。  
  
    レポートの生成の詳細については、「[レポートの生成 &#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md)」を参照してください。  
  
    **注:**  
  
    -   変数値ファイルのコマンドライン引数がコンソールアプリケーションに渡され、変数がユーザーが指定した値で更新されていることを確認します。  
  
    -   サーバー接続ファイルのコマンドライン引数がコンソールアプリケーションに渡され、サーバーのパラメーター値が正しいことを確認します。  
  
-   **SqlStatementConversionSample:**  
    このサンプルを使用すると、入力と`t-sql`して指定され`sql`たソースデータベースコマンドの対応するスクリプトをユーザーが生成できます。  
  
    この`convert-sql-statement`コマンドでは、ユーザーは属性の`context`変数値 **(参照変数**mandatorily) を、ユーザーが使用しているデータベース名に変更する必要があります。 ユーザーは、変換する必要があるソース`sql`データベース`sql`コマンドに属性値を変更する必要もあります。  
  
    ユーザーは、変換する sql ファイルを指定することもできます。 これについては、 `convert-sql-statement`サンプルのコンソールスクリプトファイルのコマンド例4で説明しました。  
  
    > [!NOTE]  
    > 変数値ファイルのコマンドライン引数がコンソールアプリケーションに渡され、変数がユーザーが指定した値で更新されていることを確認します。  
  
-   **ConversionAndDataMigrationSample:**  
     このサンプルを使用すると、ユーザーはデータ移行への変換からエンドツーエンドの移行を実行できます。 変更する必要がある必須の属性値の一覧を次に示します。  
  
    **コマンド名**  
  
    `map-schema`  
  
    転送元データベースから送信先スキーマへのスキーママッピング。  
  
    **属性**  
  
    -   `source-schema:`を変換する必要があるソースデータベースを指定します。  
  
    -   `sql-server-schema`: 移行先のターゲットデータベースを指定します。  
  
    **コマンド名**  
  
    `convert-schema`  
  
    1.  送信元スキーマから送信先スキーマへのスキーマ変換を実行します。  
  
    2.  ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルの`convert-schema`コンソールスクリプトファイルの例4に示すように、複数のノードを指定できます。  
  
    **属性**  
  
    `object-name`: 変換する必要があるソースデータベースまたはオブジェクトの名前を指定します。 に指定され`object-type`ているオブジェクトの型に基づいて、対応するが変更されていることを確認します。`object-name`  
  
    **コマンド名**  
  
    `synchronize-target`  
  
    1.  ターゲットデータベースとターゲットオブジェクトを同期します。  
  
    2.  ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルコンソール`synchronize-target`スクリプトファイルのコマンド例3に示すように、複数のノードを指定できます。  
  
    **属性**  
  
    `object-name:`を作成する必要がある sql server データベースまたはオブジェクトの名前を指定します。 に指定され`object-type`ているオブジェクトの型に基づいて、対応するが変更されていることを確認します。`object-name`  
  
    **コマンド名**  
  
    `migrate-data`  
  
    1.  ソースデータをターゲットに移行します。  
  
    2.  ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルの`migrate-data`コンソールスクリプトファイルの例2に示すように、複数のノードを指定できます。  
  
    **属性**  
  
    `object-name:`移行する必要があるソースデータベースまたはテーブルの名前を指定します。 に指定され`object-type`ているオブジェクトの型に基づいて、対応するが変更されていることを確認します。`object-name`  
  
## <a name="see-also"></a>参照  
[MySQLToSQL&#41;&#40;の変数値ファイルの作成](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
[MySQLToSQL&#41;&#40;のサーバー接続ファイルの作成](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
[MySQLToSQL&#41;&#40;レポートの生成](../../ssma/mysql/generating-reports-mysqltosql.md)  
  
