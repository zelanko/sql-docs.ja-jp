---
title: "Azure Data Lake Store ファイル システム タスク |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
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
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: cbc72958f992e0b5cae12cdfc8c0996378f9708c
ms.contentlocale: ja-jp
ms.lasthandoff: 10/11/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスク

ユーザーに対してさまざまなファイル システム操作を実行できるように、Azure データ Lake Store ファイル システム タスク[Azure データ Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/)です。

Azure データ Lake Store ファイル システム タスクのコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Azure Data Lake Store ファイル システム タスクを構成します。

にパッケージを、Azure データ Lake Store ファイル システム タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 タスクをダブルクリックまたはタスクを右クリックし、選択**編集**を開くには、 **Azure データ Lake Store ファイル システム タスク エディター**  ダイアログ ボックス。

**操作**プロパティを実行するファイル システム操作を指定します。 次の操作のいずれかを選択します。

- **CopyToADLS:** ADLS にファイルをアップロードします。
- **CopyFromADLS:** ADLS からファイルをダウンロードします。

## <a name="configure-the-properties-for-the-operation"></a>操作のプロパティを構成します。
いずれの操作については、Azure Data Lake 接続マネージャーを指定する必要があります。

各操作に固有のプロパティ次に示します。

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory:**をアップロードするファイルを含むローカル ソース ディレクトリを指定します。
- **FileNamePattern:**ソース ファイルのファイル名のフィルターを指定します。 指定したパターンに一致するファイルのみアップロードされます。 ワイルドカード`*`と`?`はサポートされています。
- **SearchRecursively:**再帰的にアップロードするファイルのソース ディレクトリ内で検索するかどうかを指定します。
- **AzureDataLakeDirectory:**ファイルをアップロードする ADLS 先ディレクトリを指定します。
- **FileExpiry:** ADLS にアップロードされたファイルの有効期限日時を指定します。 このプロパティは、ファイルが決して期限切れことを示すために空白のままにします。

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory:**をダウンロードするファイルを含む ADLS ソース ディレクトリを指定します。
- **SearchRecursively:**再帰的にダウンロードするファイルのソース ディレクトリ内で検索するかどうかを指定します。
- **LocalDirectory:**ダウンロードしたファイルを保存する先のディレクトリを指定します。
