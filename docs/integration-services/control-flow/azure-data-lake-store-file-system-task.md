---
title: "Azure Data Lake Store ファイル システム タスク |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 303d3b74da3fe370d19b7602c0e11e67b63191e7
ms.openlocfilehash: ce2355de312faed9ab66991d6d0dd344ff315a55
ms.contentlocale: ja-jp
ms.lasthandoff: 08/29/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスク

**Azure データ Lake Store ファイル システム タスク**でさまざまなファイル システム操作を実行できる[Azure データ Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/)です。

**Azure データ Lake Store ファイル システム タスク**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。

にパッケージを、Azure データ Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 タスクをダブルクリックまたはタスクを右クリックし、選択**編集**をタスク エディター ダイアログ ボックスを開きます。

**操作**プロパティを実行するファイル システム操作を指定します。 次の操作はサポートされています。

* **CopyToADLS:** ADLS にファイルをアップロードします。
* **CopyFromADLS:** ADLS からファイルをダウンロードします。

いずれの操作については、Azure Data Lake 接続マネージャーを指定する必要があります。

次のとおり、プロパティの説明については各操作に固有です。

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:**をアップロードするファイルを含むソース ディレクトリを指定します。
* **FileNamePattern:**ソース ファイルのファイル名のフィルターを指定します。 指定したパターンに一致するファイルのみがアップロードされます。 ワイルドカード`*`と`?`はサポートされています。
* **SearchRecursively:**再帰的にアップロードするファイルのソース ディレクトリ内で検索するかどうかを指定します。
* **AzureDataLakeDirectory:**ファイルをアップロードする ADLS 先ディレクトリを指定します。
* **FileExpiry:**ファイルは、ADLS にアップロードされたか、このプロパティは、ファイルが決して期限切れことを示すために空白のままに有効期限の日付と時刻を指定します。

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:**をダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。
* **SearchRecursively:**再帰的にダウンロードするファイルのソース ディレクトリ内で検索するかどうかを指定します。
* **LocalDirectory:**ダウンロードしたファイルを保存する先のディレクトリを指定します。
