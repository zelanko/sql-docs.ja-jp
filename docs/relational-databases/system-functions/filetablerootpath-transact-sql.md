---
title: "FileTableRootPath (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FileTableRootPath_TSQL
- FileTableRootPath
dev_langs:
- TSQL
helpviewer_keywords:
- FileTableRootPath function
ms.assetid: 0cba908a-c85c-4b09-b16a-df1cb333c629
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2ce67b12aa19c8229969bd5b96c838447429b203
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="filetablerootpath-transact-sql"></a>FileTableRootPath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  特定の FileTable または現在のデータベースの、ルート レベルの UNC パスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
FileTableRootPath ( [ ‘[schema_name.]FileTable_name’ ], @option )  
```  
  
## <a name="arguments"></a>引数  
 *FileTable_name*  
 FileTable の名前。 *FileTable_name*の種類は**nvarchar**です。 これは省略可能なパラメーターです。 既定値は、現在のデータベースです。 指定する*schema_name*も省略可能です。 NULL を渡すことが*FileTable_name*既定パラメーター値を使用するには  
  
 *@option*  
 パスのサーバー コンポーネントの書式設定の方法を定義する整数式です。 *@option*次の値のいずれかを持つことができます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**0**|サーバー名を次のような NetBIOS 形式に変換して返します。<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDB`<br /><br /> これが既定値です。|  
|**1**|次のように、サーバー名を変換せずに返します。<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDB`|  
|**2**|次のような、完全なサーバー パスを返します。<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDB`|  
  
## <a name="return-type"></a>戻り値の型  
 **nvarchar (4000)**  
  
 データベースが Always On 可用性グループに属している場合、 **FileTableRootPath**関数は、コンピューター名の代わりに、仮想ネットワーク名 (VNN) を返します。  
  
## <a name="general-remarks"></a>全般的な解説  
 **FileTableRootPath**関数は、次の条件のいずれかが true の場合に NULL を返します。  
  
-   値*FileTable_name*が無効です。  
  
-   呼び出し元に、指定されたテーブルまたは現在のデータベースを参照するための十分な権限がない。  
  
-   FILESTREAM オプション*database_directory*現在のデータベースに対して設定されていません。  
  
 詳しくは、「 [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)」をご覧ください。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 コードとアプリケーションが現在のコンピューターとデータベースから切り離された状態を維持するには、絶対ファイル パスに依存したコードを記述しないでください。 代わりに、完全なパス、ファイルの実行時に取得を使用して、 **FileTableRootPath**と**GetFileNamespacePath**関数を併用、次の例に示すようにします。 既定では、 **GetFileNamespacePath** 関数は、データベースのルート パスの下のファイルの相対パスを返します。  
  
```sql  
USE MyDocumentDB;  
  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
@fullPath = varchar(1000);  
  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath()  
FROM DocumentStore  
WHERE Name = N’document.docx’;  
```  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 **FileTableRootPath**関数が必要です。  
  
-   特定の FileTable のルート パスを取得するために、FileTable に対する SELECT 権限が必要です。  
  
-   **db_datareader**または上位の権限を現在のデータベースのルート パスを取得します。  
  
## <a name="examples"></a>使用例  
 次の例を呼び出す方法を示して、 **FileTableRootPath**関数。  
  
```  
USE MyDocumentDB;  
-- returns “\\MYSERVER\MSSQLSERVER\MyDocumentDB”  
SELECT FileTableRootPath();  
  
-- returns “\\MYSERVER\MSSQLSERVER\MyDocumentDB\MyFileTable”  
SELECT FileTableRootPath(N'dbo.MyFileTable');  
  
-- returns “\\MYSERVER\MSSQLSERVER\MyDocumentDB\MyFileTable”  
SELECT FileTableRootPath(N'MyFileTable');  
```  
  
## <a name="see-also"></a>参照  
 [FileTable 内のディレクトリとパスの操作](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
