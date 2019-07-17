---
title: FileTableRootPath (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- FileTableRootPath_TSQL
- FileTableRootPath
dev_langs:
- TSQL
helpviewer_keywords:
- FileTableRootPath function
ms.assetid: 0cba908a-c85c-4b09-b16a-df1cb333c629
author: rothja
ms.author: jroth
ms.openlocfilehash: 80651e82fb643d044f4c953481dde2114adcadda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042863"
---
# <a name="filetablerootpath-transact-sql"></a>FileTableRootPath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  特定の FileTable または現在のデータベースのルート レベルの UNC パスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
FileTableRootPath ( [ '[schema_name.]FileTable_name' ], @option )  
```  
  
## <a name="arguments"></a>引数  
 *FileTable_name*  
 FileTable の名前。 *FileTable_name*の種類は**nvarchar**します。 これは省略可能なパラメーターです。 既定値は、現在のデータベースです。 指定する*schema_name*も省略可能です。 NULL を渡すことが*FileTable_name*パラメーターの既定値を使用するには  
  
 *@option*  
 パスのサーバー コンポーネントの書式設定を定義する整数式。 *@option* 次の値のいずれかを設定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|サーバー名を次のような NetBIOS 形式に変換して返します。<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDatabase`<br /><br /> これは既定値です。|  
|**1**|次のように、サーバー名を変換せずに返します。<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDatabase`|  
|**2**|次のような、完全なサーバー パスを返します。<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDatabase`|  
  
## <a name="return-type"></a>戻り値の型  
 **nvarchar (4000)**  
  
 データベースが Always On 可用性グループに属している場合、 **FileTableRootPath**関数は、コンピューター名の代わりに、仮想ネットワーク名 (VNN) を返します。  
  
## <a name="general-remarks"></a>全般的な解説  
 **FileTableRootPath**関数は、次の条件のいずれかが true の場合に NULL を返します。  
  
-   値*FileTable_name*が無効です。  
  
-   呼び出し元に、指定されたテーブルまたは現在のデータベースを参照するための十分な権限がない。  
  
-   FILESTREAM オプション*database_directory*現在のデータベースに設定されていません。  
  
 詳しくは、「 [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)」をご覧ください。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 コードとアプリケーションが現在のコンピューターとデータベースから切り離された状態を維持するには、絶対ファイル パスに依存したコードを記述しないでください。 代わりに、完全なパス、ファイルの実行時に取得を使用して、 **FileTableRootPath**と**GetFileNamespacePath**関数を併用、次の例に示すようにします。 既定では、 **GetFileNamespacePath** 関数は、データベースのルート パスの下のファイルの相対パスを返します。  
  
```sql  
USE MyDocumentDatabase;  
  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
@fullPath = varchar(1000);  
  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath()  
FROM DocumentStore  
WHERE Name = N'document.docx';  
```  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 **FileTableRootPath**関数が必要です。  
  
-   特定の FileTable のルート パスを取得する、FileTable に対するアクセス許可を選択します。  
  
-   **db_datareader**または上位の権限を現在のデータベースのルート パスを取得します。  
  
## <a name="examples"></a>使用例  
 次の例を呼び出す方法を示して、 **FileTableRootPath**関数。  
  
```  
USE MyDocumentDatabase;  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase"  
SELECT FileTableRootPath();  
  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable"  
SELECT FileTableRootPath(N'dbo.MyFileTable');  
  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable"  
SELECT FileTableRootPath(N'MyFileTable');  
```  
  
## <a name="see-also"></a>関連項目  
 [FileTable 内のディレクトリとパスの操作](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
