---
title: Azure Data Lake Store ファイル システム タスク | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
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
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: e1331900994e61eacb66d0cc4efe5e49fc20e508
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスク

Azure Data Lake Store ファイル システム タスクでは、ユーザーは [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/) でさまざまなファイル システム操作を実行できます。

Azure Data Lake Store ファイル システム タスクは、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスクの構成

パッケージに Azure Data Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 次に、タスクをダブルクリックするか、右クリックして **[編集]** を選択し、**[Azure Data Lake Store File System Task Editor]\(Azure Data Lake Store ファイル システム タスク エディター\)** ダイアログ ボックスを開きます。

**[操作]** プロパティでは、実行するファイル システム操作を指定します。 以下の操作のいずれかを選択します。

- **CopyToADLS:** ADLS にファイルをアップロードします。
- **CopyFromADLS:** ADLS からファイルをダウンロードします。

## <a name="configure-the-properties-for-the-operation"></a>操作のプロパティの構成
操作に対して、Azure Data Lake 接続マネージャーを指定する必要があります。

各操作に固有のプロパティを以下に示します。

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory:** アップロードするファイルを含むローカル ソース ディレクトリを指定します。
- **FileNamePattern:** ソース ファイルのファイル名フィルターを指定します。 名前が指定されたパターンと一致するファイルのみがアップロードされます。 ワイルドカードの `*` と `?` がサポートされています。
- **SearchRecursively:** アップロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
- **AzureDataLakeDirectory:** ファイルのアップロード先となる ADLS ディレクトリを指定します。
- **FileExpiry:** ADLS にアップロードされたファイルの有効期限の日時を指定します。 ファイルの有効期限が切れないようにする場合は、このプロパティを空白のままにします。

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory:** ダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。
- **SearchRecursively:** ダウンロードするファイルのソース ディレクトリ内で再帰的に検索するかどうかを指定します。
- **LocalDirectory:** ダウンロードしたファイルの格納先となるディレクトリを指定します。
