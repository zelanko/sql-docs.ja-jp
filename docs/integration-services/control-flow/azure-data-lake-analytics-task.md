---
title: Azure Data Lake Analytics タスク | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 395d790069294aed541f9756fa7caefbb62f9a7b
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854422"
---
# <a name="azure-data-lake-analytics-task"></a>Azure Data Lake Analytics タスク

Azure Data Lake Analytics タスクを使うと、U-SQL ジョブを Azure Data Lake Analytics サービスに送信できます。 [Azure Data Lake Analytics (ADLA)](https://azure.microsoft.com/services/data-lake-analytics/)。

Azure Data Lake Analytics タスクは、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。

## <a name="configure-the-azure-data-lake-analytics-task"></a>Azure Data Lake Analytics タスクを構成する

パッケージに Azure Data Lake Analytics タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 次に、タスクをダブルクリックするか、右クリックして **[編集]** を選択し、**[Azure Data Lake Analytics Task Editor]\(Azure Data Lake Analytics タスク エディター\)** ダイアログ ボックスを開きます。 プロパティは、SSIS デザイナーを使用して、またはプログラムによって設定できます。

## <a name="general-page-configuration"></a>全般ページの構成

**[全般]** ページを使って、Azure Data Lake Analytics タスクを構成し、タスクが送信する U-SQL スクリプトを指定します。 U-SQL 言語について詳しくは、[U-SQL 言語のリファレンス](https://msdn.microsoft.com/azure/data-lake-analytics/u-sql/u-sql-language-reference)をご覧ください。

### <a name="basic-configuration"></a>基本構成

- **Name:** Azure Data Lake Analytics タスクの名前を指定します。
- **Description:** Azure Data Lake Analytics タスクの説明を指定します。

### <a name="u-sql-configuration"></a>U-SQL の構成

U-SQL の構成には、**SourceType** と、**SourceType** の値に基づく動的なオプションの、2 つの設定があります。 

- **SourceType:** U-SQL スクリプトのソースを指定します。 スクリプトは、SSIS パッケージの実行中に、Azure Data Lake Analytics アカウントに送信されます。 このプロパティには、次の表に示す 3 つのオプションがあります。

|ReplTest1|[説明]|  
|-----------|-----------------|  
|**DirectInput (直接入力)**|インライン エディターを使用して U-SQL スクリプトを指定します。 この値を選択すると、動的オプション **[USQLStatement]** が表示されます。|  
|**[FileConnection]**|U-SQL スクリプトを含むローカルな .usql ファイルを指定します。 この値を選択すると、動的オプション **[FileConnection]** が表示されます。|  
|**変数**|U-SQL スクリプトを含む SSIS 変数を指定します。 この値を選択すると、動的オプション **[SourceVariable]** が表示されます。|

- **SourceType 動的オプション:** U-SQL クエリのスクリプトの内容を指定します。 

|[SourceType]|動的オプション|  
|-----------|-----------------|  
|**SourceType = DirectInput**|送信する U-SQL クエリを、オプション ボックスに直接入力します。または、参照ボタン [...] をクリックし、**[Enter U-SQL Query]\(U-SQL クエリの入力\)** ダイアログ ボックスで U-SQL クエリを入力します。|  
|**SourceType = FileConnection**|既存のファイル接続マネージャーを選択するか、<**新しい接続…**> をクリックして新しい接続を作成します。 **関連記事:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)|  
|**SourceType = Variable**|既存の変数を選択するか、\<**新しい変数...**> をクリックして新しい変数を作成します。 **関連記事:** [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)|


### <a name="job-configuration"></a>ジョブの構成
ジョブの構成では、U-SQL ジョブの送信のプロパティを指定します。

- **AzureDataLakeAnalyticsConnection:** U-SQL スクリプト送信先の Azure Data Lake Analytics アカウントを指定します。 定義済みの接続マネージャーの一覧から接続を選択します。 新しい接続を作成するには、<**新しい接続**> を選択します。 関連記事: [Azure Data Lake Analytics 接続マネージャーを構成する](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)。

- **JobName:** U-SQL ジョブの名前を指定します。 
- **AnalyticsUnits:** U-SQL ジョブの分析ユニット数を指定します。
- **Priority:** U-SQL ジョブの優先順位を指定します。 0 ～ 1000 の優先順位を設定でき、小さい値ほど優先順位は高くなります。
- **RuntimeVersion:** U-SQL ジョブの Azure Data Lake Analytics ランタイム バージョンを指定します。 既定では、"default" に設定されます。 通常、このプロパティを変更する必要はありません。
- **Synchronous:** このブール値は、タスクがジョブの実行の完了を待つかどうかを指定します。 True に設定すると、タスクはジョブ完了後に成功としてマークされます。 False に設定すると、タスクはジョブが準備フェーズを経過した後で成功としてマークされます。

|ReplTest1|[説明]|
|-----------|-----------------|
|True|タスクの結果は、U-SQL ジョブの実行結果に基づきます。 ジョブ成功 --> タスク成功、ジョブ失敗 --> タスク失敗、タスク成功または失敗 --> タスク完了。|
|False|タスクの結果は、U-SQL ジョブの送信と準備の結果に基づきます。 ジョブ送信が成功して準備フェーズを通過 --> タスク成功、ジョブ送信が失敗またはジョブが準備フェーズで失敗 --> タスク失敗、タスク成功または失敗 --> タスク完了。|

- **TimeOut:** ジョブ実行のタイムアウト時間を秒単位で指定します。 ジョブがタイムアウトすると、ジョブは取り消され、タスクは失敗としてマークされます。同期が False に設定されている場合、タイムアウト プロパティは使用できません。 **Synchronous** が **false** に設定されている場合、タイムアウト プロパティは使用できません。

## <a name="parameter-mapping-page-configuration"></a>パラメーター マッピング ページの構成

**[Azure Data Lake Analytics Task Editor]\(Azure Data Lake Analytics タスク エディター\)** ダイアログ ボックスの **[パラメーター マッピング]** ページを使用して、U-SQL スクリプトのパラメーター (U-SQL 変数) に変数をマップします。

- **[変数名]:** **[追加]** をクリックしてパラメーター マッピングを追加した後で、システム変数またはユーザー定義変数を一覧から選択するか、\<**新しい変数...**> をクリックして **[変数の追加]** ダイアログ ボックスで新しい変数を追加します。 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)  

- **[パラメーター名]:** U-SQL スクリプトのパラメーター/変数名を指定します。 パラメーター名が @ 記号で始まっていることを確認します (例: @Param1)。 

U-SQL スクリプトにパラメーターを渡す方法の例を次に示します。

**U-SQL スクリプトのサンプル**
```
@searchlog =
    EXTRACT UserId          int,
            Start           DateTime,
            Region          string,
            Query           string,
            Duration        int,
            Urls            string,
            ClickedUrls     string
    FROM @in
    USING Extractors.Tsv(nullEscape:"#NULL#");

@rs1 =
    SELECT Start, Region, Duration
    FROM @searchlog
WHERE Region == "en-gb";

@rs1 =
    SELECT Start, Region, Duration
    FROM @rs1
    WHERE Start <= DateTime.Parse("2012/02/19");

OUTPUT @rs1   
    TO @out
      USING Outputters.Tsv(quoting:false, dateTimeFormat:null);
```

上のスクリプト例では、入力と出力のパスが **@in** および **@out** パラメーターで定義されています。 U-SQL スクリプトの **@in** および **@out** パラメーターの値は、パラメーター マッピングの構成に従って動的に渡されます。

|[変数名]|[パラメーター名]|
|-------------|--------------|
|ユーザー: Variable1|@in|
|ユーザー: Variable2|@out| 

## <a name="expression-page-configuration"></a>式ページの構成

[全般] ページの構成のすべてのプロパティをプロパティ式として割り当てて、実行時のプロパティの動的な更新を有効にできます。 **関連トピック:** [パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)

## <a name="see-also"></a>参照
- [Azure Data Lake Analytics 接続マネージャー](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)
- [Azure Data Lake Store ファイル システム タスク](../../integration-services/control-flow/azure-data-lake-store-file-system-task.md)
- [Azure Data Lake Store 接続マネージャー](../../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

