---
title: "Azure BLOB ストレージのデータに一括アクセスする例 | Microsoft Docs"
ms.custom: 
ms.date: 01/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: import-export
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bulk importing [SQL Server], from Azure blob storage
- Azure blob storage, bulk import to SQL Server
- BULK INSERT, Azure blob storage
- OPENROWSET, Azure blob storage
ms.assetid: f7d85db3-7a93-400e-87af-f56247319ecd
caps.latest.revision: 2
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: ece80f578fc797dcd721dfb3f831e9bf3937abd1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/14/2017

---
# <a name="examples-of-bulk-access-to-data-in-azure-blob-storage"></a>Azure BLOB ストレージのデータに一括アクセスする例
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

`BULK INSERT` ステートメントと `OPENROWSET` ステートメントは、Azure BLOB ストレージのファイルに直接アクセスできます。 次の例では、`inv-2017-01-19.csv` という名前の CSV (コンマ区切り値) ファイルのデータを使用します。このファイルは `newinvoices` という名前のストレージ アカウントで `Week3` という名前のコンテナーに格納されています。 ファイルの書式を設定するパスを使用できますが、以下の例には含まれていません。 

SQL Server から Azure BLOB ストレージに一括アクセスする場合、[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 以上が必要になります。

## <a name="create-the-credential"></a>資格情報を作成する   
   
下のすべての例で、Shared Access Signature を参照するデータベース スコープ資格情報が必要です。   

>  [!IMPORTANT]
>  外部データ ソースは、`SHARED ACCESS SIGNATURE` ID を使用するデータベース スコープ資格情報で作成する必要があります。 ストレージ アカウントの Shared Access Signature を作成するには、Azure ポータルのストレージ アカウント プロパティに関するページで **Shared Access Signature** プロパティを参照してください。 Shared Access Signature に関する詳細については、「[Shared Access Signature (SAS) を使用](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)」を参照してください。 資格情報の詳細については、「[CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)」 (データベース スコープ資格情報を作成する) を参照してください。  
 
`IDENTITY` (`SHARED ACCESS SIGNATURE` に設定します) を利用してデータベース スコープ資格情報を作成します。 Azure ポータルのシークレットを使用します。 例:  

```sql
CREATE DATABASE SCOPED CREDENTIAL UploadInvoices  
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'QLYMgmSXMklt%2FI1U6DcVrQixnlU5Sgbtk1qDRakUBGs%3D';
```


## <a name="accessing-data-in-a-csv-file-referencing-an-azure-blob-storage-location"></a>Azure BLOB ストレージの場所を参照する CSV ファイルのデータにアクセスする   
次の例では、`newinvoices` という名前の Azure ストレージ アカウントを指す外部データ ソースを使用します。   
```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net', 
        CREDENTIAL = UploadInvoices  
    );
```   

次に、`OPENROWSET` ステートメントがコンテナー名 (`week3`) をファイルの説明に追加します。 ファイルの名前は `inv-2017-01-19.csv` です。
```sql     
SELECT * FROM OPENROWSET(
   BULK  'week3/inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   SINGLE_CLOB) AS DataFile;
```

`BULK INSERT` を利用し、コンテナーとファイルの説明を使用します。

```sql
BULK INSERT Colors2
FROM 'week3/inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoices',
      FORMAT = 'CSV'); 
```

## <a name="accessing-data-in-a-csv-file-referencing-a-container-in-an-azure-blob-storage-location"></a>Azure BLOB ストレージの場所にあるコンテナーを参照する CSV ファイルのデータにアクセスする   

次の例では、Azure ストレージ アカウントにあるコンテナー (`week3` という名前) を指す外部データ ソースを使用します。   
```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoicesContainer
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3', 
        CREDENTIAL = UploadInvoices  
    );
```  
  
`OPENROWSET` ステートメントはコンテナー名をファイルの説明に追加しません。
```sql
SELECT * FROM OPENROWSET(
   BULK  'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoicesContainer',
   SINGLE_CLOB) AS DataFile;
```   

`BULK INSERT` を利用し、ファイルの説明にコンテナー名を使用しません。 

```sql
BULK INSERT Colors2
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoicesContainer',
      FORMAT = 'CSV'); 
```

## <a name="see-also"></a>参照   

[データベース スコープ資格情報を作成する](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
[外部データ ソースを作成する](../../t-sql/statements/create-external-data-source-transact-sql.md)   
[一括挿入](../../t-sql/statements/bulk-insert-transact-sql.md)   
[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)   


