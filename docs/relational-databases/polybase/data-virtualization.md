---
title: SQL Server 2019 CTP 2.0 で外部データを仮想化する | Microsoft Docs
description: ''
author: Abiola
ms.author: aboke
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: polybase
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: dfd4460c51e4aeef8e9faff8479e7edf2678c35f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627320"
---
# <a name="use-the-data-external-table-wizard-with-external-tables"></a>外部テーブルでデータ外部テーブル ウィザードを使用する

SQL Server 2019 CTP 2.0 の主なシナリオの 1 つは、データを仮想化する機能です。  このプロセスでは、データを元の場所に置いたまま、SQL Server インスタンスでデータを**仮想化**して、SQL Server 内の他のテーブルと同じようにクエリを行うことができます。 これにより、ETL プロセスの必要性が最小になります。 これは、Polybase コネクタを使用することによって可能です。 データの仮想化について詳しくは、「[PolyBase の概要](polybase-guide.md)」をご覧ください。

## <a name="launch-the-external-table-wizard"></a>外部テーブル ウィザードを起動する

配置スクリプトの最後で取得される IP アドレス/ポート番号 (31433) を使用して、マスター インスタンスに接続します。 オブジェクト エクスプローラーで **[データベース]** ノードを展開します。 次に、既存の SQL Server インスタンスからのデータを仮想化するデータベースのいずれかを選択します。 データベースを右クリックして、コンテキスト メニューから **[Create External Table]\(外部テーブルの作成\)** を選択します。 これにより、データ仮想化ウィザードが起動します。 コマンド パレットで Ctrl + Shift + P (Windows) キーまたは Cmd + Shift + P (Mac) キーを押して、データ仮想化ウィザードを起動することもできます。

![データ仮想化ウィザード](media/data-virtualization/virtualize-data-wizard.png)
## <a name="select-a-data-source"></a>データ ソースを選択する

データベースのいずれかからウィザードを起動した場合、出力先ドロップダウンが自動入力されていることがわかります。 また、この画面では出力先データベースを入力または変更できます。 ウィザードでサポートされている外部データ ソースの種類は、SQL Server と Oracle です。

> [!NOTE]
>SQL Server が既定で強調表示されます


![データ ソースを選択する](media/data-virtualization/select-data-source.png)

[次へ] をクリックしてウィザードの次のステップに進み、データベースのマスター キーを設定します。

## <a name="create-database-master-key"></a>データベースのマスター キーを作成する

このステップでは、データベースのマスター キーの作成を求められます。 マスター キーの作成は必須です。これにより、外部データ ソースによって使用される資格情報がセキュリティ保護されます。 マスター キーには強力なパスワードを選択してください。 また、BACKUP MASTER KEY を使用してマスター キーをバックアップし、安全な別の場所に保存する必要があります。

![データベースのマスター キーを作成する](media/data-virtualization/virtualize-data-master-key.png)

> [!IMPORTANT]
> データベースのマスター キーが既にある場合は、入力フィールドは制限されており、このステップを省略できます。[次へ] をクリックして、ウィザードの次のページに進むことができます。

> [!NOTE]
> 強力なパスワードを選択しない場合、ウィザードは最後のステップになります。 これは既知の問題であり、今後のリリースでさらにわかりやすく修正される予定です。

## <a name="enter-the-external-data-source-credentials"></a>外部データ ソースの資格情報を入力する

このステップでは、外部データ ソースと資格情報の詳細を入力してください。 このステップでは、外部データ ソース オブジェクトを作成し、そのデータベース オブジェクトの資格情報を使用してデータ ソースに接続します。 外部データ ソースの名前を (例: Test) を指定し、外部データ ソースの SQL Server 接続の詳細 (サーバー名と、そのサーバー上で作成する外部データ ソースのデータベース名) を指定します。

次のステップは資格情報の構成なので、作成している外部データ ソースのサインイン情報を安全に格納するために使用されるデータベース スコープの資格情報の名前である資格情報名 (例: TestCred) と、データ ソースに接続するためのユーザー名とパスワードを指定します。

![外部データ ソースの資格情報](media/data-virtualization/data-source-credentials.png)

## <a name="external-data-table-mapping"></a>外部データ テーブルのマッピング

次のウィンドウでは、外部ビューを作成するテーブルを選択します。 親データベースを選択すると、すべての子テーブルも含まれます。 テーブルを選択するときは、右側でマッピング テーブルを確認できます。 ここでは、"型" の変更を行ったり、選択した外部テーブル自体の名前を変更したりできます。

![外部データ ソースの資格情報](media/data-virtualization/data-table-mapping.png)

> [!NOTE]
>選択した別のテーブルをダブルクリックすると、マッピング ビューが変わります。

> [!IMPORTANT]
>外部テーブル ツールでは、写真型はまだサポートされていません。 写真型が含まれる外部ビューを作成すると、テーブル作成後にエラーがスローされます。 その場合でもテーブルは作成されます。

## <a name="summary"></a>[概要]

このステップでは、選択内容の要約が提供されます。 データベース スコープの資格情報の名前と、出力先データベースに作成される外部データ ソース オブジェクトが提供します。 このステップでは、**[スクリプトの生成]** オプションを選択すると外部データ ソースを作成する構文が T-SQL でスクリプト化され、**[作成]** を選択すると外部データ ソース オブジェクトが作成されます。

![概要画面](media/data-virtualization/virtualize-data-summary.png)

[作成] をクリックした場合は、出力先データベースに作成された外部データ ソース オブジェクトを確認できます。

![外部データ ソース](media/data-virtualization/external-data-sources.png)

**[スクリプトの生成]** をクリックした場合は、外部データ ソース オブジェクトを作成するために生成される T-SQL クエリを確認できます。

![スクリプトの生成](media/data-virtualization/generated-script.png)

> [!NOTE]
> [スクリプトの生成] は、ウィザードの最後のページにのみ表示されるべきです。 現在は、すべてのページに表示されます。

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターおよび関連するシナリオについて詳しくは、「[SQL Server ビッグ データ クラスターとは](../../big-data-cluster/big-data-cluster-overview.md)」をご覧ください。
