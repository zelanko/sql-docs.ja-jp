---
title: コマンドライン (SQL Server) から Data Migration Assistant を実行 |Microsoft Docs
description: SQL Server データベースの移行を評価するためのコマンドラインから Data Migration Assistant を実行する方法について説明します
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 6b364dc03d48cbc1c0487362712e10f7ab0b782e
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785463"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>コマンドラインから Data Migration Assistant を実行します。
Data Migration Assistant をインストールするバージョン 2.1 以降で、ときで dmacmd.exe もインストールされます *%programfiles%\\Microsoft Data Migration Assistant\\*します。 Dmacmd.exe を使用して、無人モードでデータベースを評価し、JSON または CSV ファイルに結果を出力します。 このメソッドは、いくつかのデータベースや巨大なデータベースを評価するときに便利です。 

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


|引数  |説明  | 必須 (はい/いいえ)
|---------|---------|---------------|
| `/help or /?`     | Dmacmd.exe ヘルプ テキストを使用する方法        | ×
|`/AssessmentName`     |   評価プロジェクトの名前   | Y
|`/AssessmentDatabases`     | 接続文字列のスペースで区切られた一覧。 データベース名 (初期カタログ) と小文字は区別されます。 | Y
|`/AssessmentTargetPlatform`     | 評価では、サポートされている値のターゲット プラットフォーム: SqlServer2012、SqlServer2014、SqlServer2016、および AzureSqlDatabaseV12 します。 既定値は SqlServer2016   | ×
|`/AssessmentEvaluateFeatureParity`  | 機能パリティ ルールを実行します。  | ×
|`/AssessmentEvaluateCompatibilityIssues`     | 互換性規則を実行します。  | Y <br> (AssessmentEvaluateCompatibilityIssues または AssessmentEvaluateRecommendations が必要です)。
|`/AssessmentEvaluateRecommendations`     | 機能のお勧めを実行します。        | Y <br> (AssessmentEvaluateCompatibilityIssues または必要な AssessmentEvaluateRecommendationsis)
|`/AssessmentOverwriteResult`     | 結果ファイルを上書きします    | ×
|`/AssessmentResultJson`     | JSON の結果ファイルへの完全パス     | Y <br> (AssessmentResultJson または AssessmentResultCsv のいずれかが必要)
|`/AssessmentResultCsv`    | CSV 結果ファイルへの完全パス   | Y <br>(AssessmentResultJson または AssessmentResultCsv のいずれかが必要)




## <a name="examples"></a>使用例

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Windows 認証と実行の互換性規則を使用して単一データベースの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```



**SQL Server 認証と実行機能の推奨事項を使用して単一データベースの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```


**ターゲット プラットフォームの SQL Server 2012 では、単一データベースの評価結果を .json および .csv のファイルに保存します。**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
```


**ターゲット プラットフォームは、SQL Azure データベースの単一データベースの評価結果を .json および .csv のファイルに保存します。**

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
