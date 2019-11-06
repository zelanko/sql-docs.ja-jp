---
title: Azure SQL Managed Instance 拡張機能
titleSuffix: Azure Data Studio
description: Azure SQL Managed Instance で Azure Data Studio を使用します
ms.custom: seodec18
ms.date: 10/07/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: jovanpop-msft
ms.author: jovanpop
manager: alanyu
ms.openlocfilehash: d443292fb091679d3d6a18d557a5a7aac464fdec
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041141"
---
# <a name="managed-instance-support-for-azure-data-studio-preview"></a>Azure Data Studio に対する Managed Instance のサポート (プレビュー)

この拡張機能を使用すると、[Azure Data Studio](https://github.com/Microsoft/azuredatastudio) で [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index) を使用できるようになります。 この拡張機能には次の機能があります。

- Managed Instance のプロパティの表示 (仮想コア、使用済みストレージ)。
- 過去 2 時間の CPU およびストレージの使用量の監視。
- 構成に関する警告およびチューニングの推奨事項の表示。
- データベース レプリカの状態の表示。
- フィルター処理されたエラー ログの表示。

## <a name="installations"></a>インストール

Managed Instance 拡張機能の公式リリースをインストールするには、[Azure Data Studio のドキュメント](https://docs.microsoft.com/sql/azure-data-studio/extensions)の手順に従います。
[機能拡張] ウィンドウで「Managed Instance」拡張機能を検索し、そこでインストールします。  今後、拡張機能の更新があれば、自動的に通知されます。

Managed Instance 拡張機能をインストールすると、Azure Data Studio に [`Managed Instance`] タブが表示されます。 このタブでは、Managed Instance に固有の情報を確認できます。

## <a name="properties"></a>Properties

この拡張機能を使用すると、Managed Instance の技術的特性といくつかのリソース使用量を見ることができます。

![Managed Instance のプロパティ](media/azure-sql-mi-extension/ads-mi-tab1.png)

最初のブレードでは、次の詳細を見ることができます。

- **基本的なプロパティ**: 使用可能な仮想コア数、メモリ、ストレージ、現在のサービス レベルとハードウェアの世代、インスタンス ログ書き込みスループットやファイル IO/スループットなどの IO 特性。
- **ローカル SSD ストレージの使用量**: General Purpose サービス レベルでは **TEMPDB** ファイルだけがローカル環境に配置されますが、Business Critical レベルではすべてのデータベース ファイルがローカル SSD ストレージに配置されます。 このセクションでは、Managed Instance によって使用されているローカル ストレージの容量を確認できます。
- **Azure Premium Disk Storage の使用量**: General Purpose サービス レベルのユーザー データベースとシステム データベースは、Azure Premium Storage に配置されます。 ここでは、使用したデータの量と、残っているストレージとファイルの数を確認できます。 Business Critical サービス レベルでは、このセクションには何も表示されません。
- **リソース使用量**: 過去 2 時間以内にインスタンスで使用されたストレージと CPU の量が表示されます。 制限に達している場合は、インスタンスのサイズを増やします。

## <a name="recommendations"></a>推奨事項

この拡張機能で提供される推奨事項とアラートは、Managed Instance の最適化に役立ちます。

![Managed Instance の推奨事項](media/azure-sql-mi-extension/ads-mi-tab2.png)

このテーブルに示される推奨事項の一部を次に示します。

- ストレージ領域の制限に到達 - データベースがストレージの制限に達した場合、読み取りクエリでさえ処理できない可能性があるため、不要なデータを削除するか、インスタンスのストレージ サイズを増やす必要があります。
- インスタンスのスループット制限に到達 - 読み込みが GP で 22 MB/秒、BC で 48 MB/秒になった場合は、バックアップを実行できるように、Managed Instance によって負荷が制限されます。
- メモリ不足 - ページの予測保持期間が低い場合、または `PAGEIOLATCH` 待機統計が高い場合は、インスタンスでページがメモリから削除され、定常的にディスクから多くのページの読み込みが試みられていることを示している可能性があります。
- ログ ファイルの制限 - ログが [General Purpose サービス レベルのファイル IO 制限](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier)に達している場合、パフォーマンスを向上させるにはファイル サイズを増やすことが必要な場合があります。
- データ ファイルの制限 - データ ファイルが [General Purpose サービス レベルのファイル IO 制限](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier)に達している場合、パフォーマンスを向上させるにはファイル サイズを増やすことが必要な場合があります。 この問題によって、メモリ不足が発生し、バックアップの速度が低下している可能性があります。
- 可用性の問題 - 仮想ログ ファイルの数が多いと、パフォーマンスに影響があり、プロセスで障害が発生した場合に、General Purpose サービス レベルでのデータベース復旧に時間がかかる可能性があります。

これらの推奨事項を定期的に確認し、根本原因を調査して、是正措置を講じる必要があります。 Managed Instance 拡張機能では、報告された問題の一部を軽減するために実行できるスクリプトが提供されています。

## <a name="replicas"></a>レプリカ

Managed Instance 拡張機能を使用すると、お使いのマネージド インスタンス内のデータベース レプリカの状態を確認できます。

![Managed Instance のレプリカ](media/azure-sql-mi-extension/ads-mi-tab3.png)

General Purpose サービス レベルでは、すべてのデータベースに 1 つの (プライマリ) レプリカがあります。Business Critical のインスタンスでは、すべてのデータベースに 1 つのプライマリ レプリカと 3 つのセカンダリ レプリカがあります (1 つは読み取り専用ワークロードに使用されます)。 ここでは、同期プロセスを監視し、すべてのセカンダリ レプリカがプライマリ レプリカと同期されていることを確認できます。

## <a name="logs"></a>ログ

Managed Instance 拡張機能では、最も関連性の高い最新の SQL エラー ログ エントリが表示されます。

![Managed Instance のログ エントリ](media/azure-sql-mi-extension/ads-mi-tab4.png)

Managed Instance では大量のログ エントリが出力され、そのほとんどは内部/システムの情報です。 一部のログ エントリでは、実際の論理データベース名ではなく、物理データベース名 (`GUID` の値) が示されます。

Managed Instance 拡張機能では、[Dimitri Furman 法](https://techcommunity.microsoft.com/t5/DataCAT/Azure-SQL-DB-Managed-Instance-sp-readmierrorlog/ba-p/305506)に基づいて不要なログ エントリが除外され、物理名ではなく実際の論理ファイル名が表示されます。

## <a name="reporting-problems"></a>問題の報告

Managed Instance 拡張機能に関して問題が発生した場合は、[Extension GitHub プロジェクト](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/issues)で問題を報告してください。

## <a name="maintainers"></a>保守担当者

- [Jovan Popovic (MSFT)](https://github.com/jovanpop_msft) - [@jovanpop_msft](https://twitter.com/JovanPop_MSFT)

## <a name="code-of-conduct"></a>倫理規定

このプロジェクトは、「[Microsoft のオープン ソースの倫理規定][conduct-code]」を採用しています。
詳細については、[倫理規定の FAQ][conduct-FAQ] のページを参照してください。また、追加の質問やコメントがある場合は [opencode@microsoft.com][conduct-email] にお問い合わせください。

[conduct-code]: http://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: http://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
[conduct-md]: https://github.com/PowerShell/vscode-powershell/blob/master/CODE_OF_CONDUCT.md
