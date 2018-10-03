---
title: Azure Data Lake Store ファイル システム タスク | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0c6b4c27b0edde310ba3252dd67bf8f51f40f0e5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136562"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスク
**Azure Data Lake Store ファイル システム タスク**でさまざまなファイル システム操作を実行することができます[Azure Data Lake Store (ADLS)](https://azure.microsoft.com/en-us/services/data-lake-store/)します。

パッケージに Azure Data Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 タスクをダブルクリックします。 またはタスクを右クリックと選択**編集**を、タスク エディター ダイアログ ボックスを開きます。

**[操作]** プロパティでは、実行するファイル システム操作を指定します。 次の操作がサポートされています。

* **CopyToADLS:** ADLS にファイルをアップロードします。
* **CopyFromADLS:** ADLS からファイルをダウンロードします。

操作に対して、Azure Data Lake 接続マネージャーを指定する必要があります。

各操作に固有のプロパティの説明については、ここでは。

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:** をアップロードするファイルを含むソース ディレクトリを指定します。
* **FileNamePattern:** ソース ファイルのファイル名フィルターを指定します。 名前、指定したパターンに一致するファイルのみがアップロードされます。 ワイルドカードの `*` と `?` がサポートされています。
* **SearchRecursively:** アップロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
* **AzureDataLakeDirectory:** ファイルのアップロード先となる ADLS ディレクトリを指定します。
* **FileExpiry:** ADLS にアップロードするファイルまたはこのプロパティをファイルが無期限することを示す空白のままにするために、有効期限の日付と時刻を指定します。

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:** ダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。
* **SearchRecursively:** ダウンロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
* **LocalDirectory:** ダウンロードしたファイルの格納先となるディレクトリを指定します。
