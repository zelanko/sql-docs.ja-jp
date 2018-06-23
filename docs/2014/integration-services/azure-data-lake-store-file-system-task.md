---
title: Azure Data Lake Store ファイル システム タスク | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.openlocfilehash: 240780efd1b12596b0ebb6156ad98c508f0e8051
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070752"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスク
**Azure データ Lake Store ファイル システム タスク**でさまざまなファイル システム操作を実行できる[Azure データ Lake Store (ADLS)](https://azure.microsoft.com/en-us/services/data-lake-store/)です。

パッケージに Azure Data Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 タスクをダブルクリックまたはタスクを右クリックし、選択**編集**をタスク エディター ダイアログ ボックスを開きます。

**[操作]** プロパティでは、実行するファイル システム操作を指定します。 次の操作はサポートされています。

* **CopyToADLS:** ADLS にファイルをアップロードします。
* **CopyFromADLS:** ADLS からファイルをダウンロードします。

操作に対して、Azure Data Lake 接続マネージャーを指定する必要があります。

次のとおり、プロパティの説明については各操作に固有です。

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:** をアップロードするファイルを含むソース ディレクトリを指定します。
* **FileNamePattern:** ソース ファイルのファイル名フィルターを指定します。 指定したパターンに一致するファイルのみがアップロードされます。 ワイルドカードの `*` と `?` がサポートされています。
* **SearchRecursively:** アップロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
* **AzureDataLakeDirectory:** ファイルのアップロード先となる ADLS ディレクトリを指定します。
* **FileExpiry:** ファイルは、ADLS にアップロードされたか、このプロパティは、ファイルが決して期限切れことを示すために空白のままに有効期限の日付と時刻を指定します。

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:** ダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。
* **SearchRecursively:** ダウンロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
* **LocalDirectory:** ダウンロードしたファイルの格納先となるディレクトリを指定します。
