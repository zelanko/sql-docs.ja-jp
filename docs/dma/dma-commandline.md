---
title: "(SQL Server データ Migration Assistant) コマンドラインから実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/01/2017
ms.prod: sql-non-specified
ms.prod_service: dma
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: sql-dma
ms.tgt_pltfrm: 
ms.topic: article
keywords: 
helpviewer_keywords: Data Migration Assistant, Command Line
ms.assetid: 
caps.latest.revision: 
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6147d01802a363082baf27d6b909e2c98f9afef2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>コマンドラインからのデータ移行アシスタントを実行します。
データ移行のアシスタントをインストールするバージョン 2.1 以降と、ときで dmacmd.exe もインストールされます*%programfiles%\\Microsoft データ Migration Assistant\\*です。 Dmacmd.exe を使用して、無人モードでデータベースを評価し、JSON または CSV ファイルに結果を出力します。 これは、いくつかのデータベースまたは巨大なデータベースを評価するときに特に便利です。 

> [!NOTE]
> 評価のみを実行している Dmacmd.exe をサポートします。 この時点では、移行はサポートされていません。


## <a name="command-line-arguments"></a>コマンドライン引数

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```


|引数  |Description  | 必須 (はい/いいえ)
|---------|---------|---------------|
| `/help or /?`     | Dmacmd.exe ヘルプ テキストを使用する方法        | ×
|`/AssessmentName`     |   評価のプロジェクトの名前   | Y
|`/AssessmentDatabases`     | 接続文字列のスペースで区切られたリスト。 データベース名 (Initial Catalog) は、大文字小文字を区別します。 | Y
|`/AssessmentTargetPlatform`     | ターゲット プラットフォームに対する評価、サポートされる値: SqlServer2012、SqlServer2014、SqlServer2016 および AzureSqlDatabaseV12 です。 既定値は SqlServer2016   | ×
|`/AssessmentEvaluateFeatureParity`  | 機能パリティ ルールを実行します。  | ×
|`/AssessmentEvaluateCompatibilityIssues`     | 互換性規則を実行します。  | Y <br> (AssessmentEvaluateCompatibilityIssues または AssessmentEvaluateRecommendations のいずれかが必要です)
|`/AssessmentEvaluateRecommendations`     | 機能の推奨事項を実行します。        | Y <br> (AssessmentEvaluateCompatibilityIssues または AssessmentEvaluateRecommendationsis 必要)
|`/AssessmentOverwriteResult`     | 結果ファイルを上書き    | ×
|`/AssessmentResultJson`     | JSON の結果ファイルへの完全パス     | Y <br> (AssessmentResultJson または AssessmentResultCsv のいずれかが必要)
|`/AssessmentResultCsv`    | CSV 結果ファイルへの完全パス   | Y <br>(AssessmentResultJson または AssessmentResultCsv のいずれかが必要)




## <a name="examples"></a>使用例

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Windows 認証と実行の互換性の規則を使用してデータベースに 1 つの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```



**SQL Server 認証され実行されている機能の推奨事項を使用してデータベースに 1 つの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```


**単一データベースの評価対象プラットフォームで SQL Server 2012 と結果を .json と .csv ファイルに保存**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
```


**ターゲット プラットフォーム SQL Azure データベースのデータベースに 1 つの評価結果を .json と .csv ファイルに保存します。**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="AzureSqlDatabaseV12"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"
```


**複数データベースの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
***/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"***
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```



## <a name="see-also"></a>参照

[データ移行アシスタントをダウンロード](https://www.microsoft.com/download/details.aspx?id=53595)
