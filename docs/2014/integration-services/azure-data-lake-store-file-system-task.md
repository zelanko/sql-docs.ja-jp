---
title: Azure Data Lake Store ファイル システム タスク | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 69a521cb72e68141f5706f5187a0288a3f44f241
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66061374"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスク

**Azure Data Lake Store ファイルシステムタスク**を使用すると、ユーザーは[Azure Data Lake Store (adls)](https://azure.microsoft.com/services/data-lake-store/)に対してさまざまなファイルシステム操作を実行できます。

パッケージに Azure Data Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 次に、タスクをダブルクリックするか、タスクを右クリックして [**編集**] を選択し、[タスクエディター] ダイアログボックスを開きます。

**[操作]** プロパティでは、実行するファイル システム操作を指定します。 次の操作がサポートされています。

* **CopyToADLS:** ADLS にファイルをアップロードします。
* **CopyFromADLS:** ADLS からファイルをダウンロードします。

操作に対して、Azure Data Lake 接続マネージャーを指定する必要があります。

各操作に固有のプロパティの説明を次に示します。

## <a name="copytoadls"></a>CopyToADLS

* **Localdirectory:** アップロードするファイルが格納されているソースディレクトリを指定します。
* **FileNamePattern:** ソース ファイルのファイル名フィルターを指定します。 名前が指定したパターンに一致するファイルのみがアップロードされます。 ワイルドカードの `*` と `?` がサポートされています。
* **SearchRecursively:** アップロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
* **AzureDataLakeDirectory:** ファイルのアップロード先となる ADLS ディレクトリを指定します。
* **Fileexpiry 切れ:** ADLS にアップロードされたファイルの有効期限の日付と時刻を指定します。または、ファイルが期限切れにならないことを示すために、このプロパティを空白のままにします。

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory:** ダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。
* **SearchRecursively:** ダウンロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
* **LocalDirectory:** ダウンロードしたファイルの格納先となるディレクトリを指定します。
