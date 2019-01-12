---
title: Azure Data Lake Store ファイル システム タスク | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
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
ms.openlocfilehash: f1b3fc1317e4454008a628c03e189e690bfeb21d
ms.sourcegitcommit: 1f53b6a536ccffd701fc87e658ddac714f6da7a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54206278"
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスク

**Azure Data Lake Store ファイル システム タスク**でさまざまなファイル システム操作を実行することができます[Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/)します。

パッケージに Azure Data Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 タスクをダブルクリックします。 またはタスクを右クリックと選択**編集**を、タスク エディター ダイアログ ボックスを開きます。

**[操作]** プロパティでは、実行するファイル システム操作を指定します。 次の操作がサポートされています。

* **CopyToADLS:** ADLS にファイルをアップロードします。
* **CopyFromADLS:** ADLS からファイルをダウンロードします。

操作に対して、Azure Data Lake 接続マネージャーを指定する必要があります。

各操作に固有のプロパティの説明については、ここでは。

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory:** アップロードするファイルを含むソース ディレクトリを指定します。
* **FileNamePattern:** ソース ファイルのファイル名フィルターを指定します。 名前、指定したパターンに一致するファイルのみがアップロードされます。 ワイルドカードの `*` と `?` がサポートされています。
* **SearchRecursively:** 再帰的にアップロードするファイルのソース ディレクトリ内で検索するかどうかを指定します。
* **AzureDataLakeDirectory:** ファイルをアップロードする ADLS 先ディレクトリを指定します。
* **FileExpiry:** このプロパティをファイルが無期限することを示す空白のままに、ADLS にアップロードされたファイルの有効期限日時を指定します。

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory:** ダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。
* **SearchRecursively:** 再帰的にダウンロードするファイルのソース ディレクトリ内で検索するかどうかを指定します。
* **LocalDirectory:** ダウンロードしたファイルの保存先のディレクトリを指定します。
