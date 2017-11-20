---
title: "Azure Blob ストレージ (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2e482b8-5f90-48c5-93fb-b412ed52659f
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 36b992b5141799d4e168b2e990643e6a515a8d69
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-azure-blob-storage-sql-server-import-and-export-wizard"></a>Azure Blob ストレージ (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **Azure Blob ストレージ**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。

>   [!NOTE]
> Azure Blob コピー元または変換先を使用するのには、SQL Server Integration Services 用 Azure Feature Pack をインストールする必要があります。
> - Feature Pack をダウンロードするを参照してください。 [Microsoft SQL Server 2016 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=49492)です。
>
> - 詳細については、「[Azure Feature Pack for Integration Services &#40;SSIS&#41; (Integration Services 用の Azure Feature Pack &#40;SSIS&#41;)](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)」を参照してください。

次のスクリーン ショットには、Azure Blob ストレージへの接続用に構成するオプションが表示されます。

![Azure BLOB ストレージ接続](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

## <a name="options-to-specify"></a>指定するオプション

> [!NOTE]
> このデータ プロバイダーの接続オプションは、Azure Blob ストレージが、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

 **Azure アカウントの使用**  
 オンライン アカウントを使用するかどうかを指定します。
  
 **ストレージ アカウント名**  
 Azure のストレージ アカウントの名前を入力します。  
  
**アカウント キー**  
Azure のストレージ アカウントのキーを入力します。  
  
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
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


