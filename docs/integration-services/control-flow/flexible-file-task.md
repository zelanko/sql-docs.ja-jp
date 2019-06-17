---
title: 柔軟なファイル タスク | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPEXTFILETASK.F1
- SQL14.DTS.DESIGNER.AFPEXTFILETASK.F1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2d01304a36f7676f53ffef3f6c6e3c600cb87cb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66411099"
---
# <a name="flexible-file-task"></a>柔軟なファイル タスク

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

柔軟なファイル タスクにより、サポートされているさまざまなストレージ サービスでファイル操作を実行できるようになります。
現在サポートされているストレージ サービスは次のとおりです。

- ローカル ファイル システム
- [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)

柔軟なファイル タスクは、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。

パッケージに柔軟なファイル タスクを追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグします。 次に、タスクをダブルクリックするか、右クリックして **[編集]** を選択し、 **[Flexible File Task Editor]\(柔軟なファイル タスク エディター\)** ダイアログ ボックスを開きます。

**[操作]** プロパティでは、実行するファイル操作を指定します。
現在サポートされているのは、**コピー**操作のみです。

**コピー**操作に対して使用できるプロパティは次のとおりです。

- **SourceConnectionType:** ソース接続マネージャーの種類を指定します。
- **SourceConnection:** ソース接続マネージャーを指定します。
- **SourceFolderPath:** ソース フォルダーのパスを指定します。
- **SourceFileName:** ソース ファイル名を指定します。 空白のままにすると、ソース フォルダーがコピーされます。
- **SearchRecursively:** サブフォルダーを再帰的にコピーするかどうかを指定します。
- **DestinationConnectionType:** 送信先接続マネージャーの種類を指定します。
- **DestinationConnection:** 送信先接続マネージャーを指定します。
- **DestinationFolderPath:** 送信先フォルダーのパスを指定します。
- **DestinationFileName:** 送信先ファイル名を指定します。
