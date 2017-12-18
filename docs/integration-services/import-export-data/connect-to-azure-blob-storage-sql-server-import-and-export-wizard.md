---
title: "Azure Blob Storage に接続する (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2e482b8-5f90-48c5-93fb-b412ed52659f
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f586df639ab239539f21f1d94155b589cd9c865
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="connect-to-azure-blob-storage-sql-server-import-and-export-wizard"></a>Azure Blob Storage に接続する (SQL Server インポートおよびエクスポート ウィザード)
このトピックでは、SQL Server インポートおよびエクスポート ウィザードの **[データ ソースの選択]** ページまたは **[変換先の選択]** ページから **Azure Blob Storage** データ ソースに接続する方法を説明します。

>   [!NOTE]
> Azure Blob Source または Azure Blob Destination を使用するには、SQL Server Integration Services 用 Azure Feature Pack をインストールする必要があります。
> - Feature Pack のダウンロード方法の詳細については、「[Microsoft SQL Server 2016 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=49492)」を参照してください。
>
> - 詳細については、「[Azure Feature Pack for Integration Services &#40;SSIS&#41; (Integration Services 用の Azure Feature Pack &#40;SSIS&#41;)](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)」を参照してください。

次のスクリーン ショットでは、Azure Blob Storage に接続するための構成オプションを示します。

![Azure BLOB ストレージ接続](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

## <a name="options-to-specify"></a>指定するオプション

> [!NOTE]
> このデータ プロバイダーの接続オプションは、Azure Blob Storage が変換元または変換先の場合でも同じです。 つまり、表示されるオプションは、ウィザードの **[データ ソースの選択]** ページまたは **[変換先の選択]** ページともに同じです。

 **Azure アカウントの使用**  
 オンライン アカウントを使用するかどうかを指定します。
  
 **ストレージ アカウント名**  
 Azure ストレージ アカウントの名前を入力します。  
  
**アカウント キー**  
Azure ストレージ アカウントのキーを入力します。  
  
 **HTTPS の使用**  
 ストレージ アカウントへの接続に HTTP または HTTPS のどちらを使用するかを指定します。  
  
 **ローカル開発者アカウントの使用**  
 ローカル コンピューター上のストレージ エミュレーターを使用するかどうかを指定します。  
  
 **BLOB コンテナーの名前**  
 指定されたストレージ アカウントで利用できるストレージ コンテナーの一覧から選択します。  
  
 **BLOB ファイル形式**  
 テキスト ファイル形式または Avro ファイル形式を選択します。  
  
 **列区切り文字**  
 テキスト形式を選択した場合は、列区切り文字を入力します。  
  
 **先頭行を列名として使用する**  
 データの最初の行に列名が含まれるかどうかを指定します。  

## <a name="see-also"></a>参照
[データ ソースの選択](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先の選択](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

