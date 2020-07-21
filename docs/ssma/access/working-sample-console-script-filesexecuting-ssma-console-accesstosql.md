---
title: SSMA コンソールのサンプルコンソールスクリプト FilesExecuting の使用 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ad75b648-d119-4119-98f0-d18f058be68d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d6fea9a78928e2944cba1571737008965d679759
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938383"
---
# <a name="working-with-the-sample-console-script-filesexecuting-the-ssma-console-accesstosql"></a>SSMA コンソールを使用したサンプルコンソールスクリプトの操作 (FilesExecuting)
ユーザー参照および使用のために、いくつかのサンプルファイルが製品と共に提供されています。 このセクションでは、エンドユーザーのニーズに合わせて、これらのスクリプトを簡単にカスタマイズする方法について説明します。  
  
## <a name="sample-console-script-files"></a>サンプルコンソールスクリプトファイル  
さまざまなシナリオをカバーする次のサンプルコンソールスクリプトファイルは、ユーザー参照用に用意されています。  
  
-   すべてのファイル  
  
-   変数の形式  
  
-   AssessmentReportGenerationSample  
  
-   ConversionAndDataMigrationSample  
  
-   **次のようにします。**  
  
    -   このサンプルでは、ソースとターゲットのデータベースで使用できるさまざまなモードの接続を提供し、ユーザーは要件に従って任意のモードを選択できます。 このサンプルには、サーバー定義が含まれています。  
  
    -   ユーザーは、必要なソースとターゲットのサーバー定義に値を変更するだけで、必要なデータベースに接続できます。 この例では、すべての値が変数の値として指定されて**います。これは、変数**に使用できます。 その他のすべての接続パラメーターは、ユーザーの作業サーバー接続ファイルから削除できます。  
  
    -   移行元サーバーと移行先サーバーへの接続の詳細については、「[サーバー接続ファイルの作成](../../ssma/access/creating-the-server-connection-files-accesstosql.md)」を参照してください &#40;&#41;。  
  
-   **変数 Valuefiles. .xml:** サンプルコンソールスクリプトファイルで使用されており、 `ServersConnectionFileSample.xml`このファイルで照合されているすべての変数。 サンプルのコンソールスクリプトを実行するには、ユーザーがサンプル変数の値をユーザー定義の変数に置き換えるだけで、このファイルを追加のコマンドライン引数としてスクリプトファイルと共に渡す必要があります。  
  
    変数値ファイルの詳細については、「 [&#41;&#40;変数値ファイルの作成](../../ssma/access/creating-variable-value-files-accesstosql.md)」を参照してください。  
  
-   **AssessmentReportGenerationSample:** このサンプルを使用すると、データの変換と移行を開始する前にユーザーが分析に使用できる xml 評価レポートを生成できます。  
  
    この`generate-assessment-report`コマンドでは、ユーザーは属性の`object-name`変数値 (mandatorily を**参照)** をユーザーが使用しているデータベース名に変更する必要があります。 指定されたオブジェクトの種類によっ`object-type`ては、値も変更する必要があります。  
  
    ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルの`generate-assessment-report`コンソールスクリプトファイルの例4に示すように、複数のノードを指定できます。  
  
    レポートの生成の詳細については、「レポートの生成」を参照してください[&#40;&#41;](../../ssma/access/generating-reports-accesstosql.md)。  
  
    > [!NOTE]  
    > -   変数値ファイルのコマンドライン引数がコンソールアプリケーションに渡され、変数がユーザーが指定した値で更新されていることを確認します。  
    > -   サーバー接続ファイルのコマンドライン引数がコンソールアプリケーションに渡され、サーバーのパラメーター値が正しいことを確認します。  
  
-   **ConversionAndDataMigrationSample:** このサンプルを使用すると、ユーザーはデータ移行への変換からエンドツーエンドの移行を実行できます。 変更する必要がある必須の属性値の一覧を次に示します。  
  
    |コマンド名|説明|属性|  
    |----------------|---------------|-------------|  
    |`map-schema`|転送元データベースから送信先スキーマへのスキーママッピング。|`source-schema:`を変換する必要があるソースデータベースを指定します。<br /><br />`sql-server-schema`: 移行先のターゲットデータベースを指定します。|  
    |`convert-schema`|送信元スキーマから送信先スキーマへのスキーマ変換を実行します。<br /><br />ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルの`convert-schema`コンソールスクリプトファイルの例4に示すように、複数のノードを指定できます。|`object-name`: 変換する必要があるソースデータベースまたはオブジェクトの名前を指定します。 に指定され`object-type`ているオブジェクトの型に基づいて、対応するが変更されていることを確認します。`object-name`|  
    |`synchronize-target`|ターゲットデータベースとターゲットオブジェクトを同期します。<br /><br />ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルコンソール`synchronize-target`スクリプトファイルのコマンド例3に示すように、複数のノードを指定できます。|`object-name:`を作成する必要がある sql server データベースまたはオブジェクトの名前を指定します。 に指定され`object-type`ているオブジェクトの型に基づいて、対応するが変更されていることを確認します。`object-name`|  
    |`migrate-data`|ソースデータをターゲットに移行します。<br /><br />ユーザーが複数のオブジェクトまたはデータベースを評価する必要がある`metabase-object`場合は、サンプルの`migrate-data`コンソールスクリプトファイルの例2に示すように、複数のノードを指定できます。|`object-name:`移行する必要があるソースデータベースまたはテーブルの名前を指定します。 に指定され`object-type`ているオブジェクトの型に基づいて、対応するが変更されていることを確認します。`object-name`|  
  
## <a name="see-also"></a>参照  
[&#41;&#40;変数値ファイルの作成](../../ssma/access/creating-variable-value-files-accesstosql.md)  
[サーバー接続ファイルを作成する &#40;、Sql&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
[&#40;にレポートを生成する Sql&#41;](../../ssma/access/generating-reports-accesstosql.md)  
  
