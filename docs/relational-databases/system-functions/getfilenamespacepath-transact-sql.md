---
title: GetFileNamespacePath (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- GetFileNamespacePath
- GetFileNamespacePath_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetFileNamespacePath function
ms.assetid: b393ecef-baa8-4d05-a268-b2f309fce89a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9c94fc80bd516c0be5b414aac98e0e4435ec8b53
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628084"
---
# <a name="getfilenamespacepath-transact-sql"></a>GetFileNamespacePath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  FileTable 内のファイルまたはディレクトリの UNC パスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<column-name>.GetFileNamespacePath(is_full_path, @option)  
```  
  
## <a name="arguments"></a>引数  
 *column-name*  
 列名、varbinary (max) の**file_stream** FileTable 内の列。  
  
 *列名*値は有効な列名である必要があります。 値が別のデータ型の列からのキャストまたは変換や、式ができません。  
  
 *is_full_path*  
 相対パスと絶対パスのどちらを返すかを指定する整数式です。 *is_full_path*値は次のいずれかであることができます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**0**|データベース レベルのディレクトリ内の相対パスを返します。<br /><br /> これは既定値です。|  
|**1**|以降では、完全な UNC パスを返します、`\\computer_name`します。|  
  
 *@option*  
 パスのサーバー コンポーネントの書式設定を定義する整数式。 *@option* 次の値のいずれかを設定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|サーバー名を次のような NetBIOS 形式に変換して返します。<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDatabase`<br /><br /> これが既定値です。|  
|**1**|次のように、サーバー名を変換せずに返します。<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDatabase`|  
|**2**|次のような、完全なサーバー パスを返します。<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDatabase`|  
  
## <a name="return-type"></a>戻り値の型  
 **nvarchar(max)**  
  
 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このパスの一部として返されるコンピューター名はクラスター化されたインスタンスの仮想ホスト名、インスタンスが、フェールオーバー クラスターでクラスター化します。  
  
 データベースが Always On 可用性グループに属している場合、 **FileTableRootPath**関数は、コンピューター名の代わりに、仮想ネットワーク名 (VNN) を返します。  
  
## <a name="general-remarks"></a>全般的な解説  
 パスを**GetFileNamespacePath**関数が、次の形式での論理ディレクトリまたはファイル パスを返します。  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\...`  
  
 この論理パスは、物理的な NTFS パスに直接対応しません。 FILESTREAM のファイル システム フィルター ドライバーと FILESTREAM エージェントによって物理パスに変換されます。 論理パスと物理パスを分離することにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、パスの有効性に影響を与えることなく内部的にデータを再構成できます。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 コードとアプリケーションが現在のコンピューターとデータベースから切り離された状態を維持するには、絶対ファイル パスに依存したコードを記述しないでください。 代わりに、完全なパス、ファイルの実行時に取得を使用して、 **FileTableRootPath**と**GetFileNamespacePath**関数を併用、次の例に示すようにします。 既定では、 **GetFileNamespacePath** 関数は、データベースのルート パスの下のファイルの相対パスを返します。  
  
```sql  
USE MyDocumentDatabase;  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
  
@fullPath = varchar(1000);  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath() FROM DocumentStore  
WHERE Name = N'document.docx';  
```  
  
## <a name="remarks"></a>コメント  
  
## <a name="examples"></a>使用例  
 次の例を呼び出す方法を示して、 **GetFileNamespacePath**ファイルまたは FileTable のディレクトリの UNC パスを取得します。  
  
```  
-- returns the relative path of the form "\MyFileTable\MyDocDirectory\document.docx"  
SELECT file_stream.GetFileNamespacePath() AS FilePath FROM DocumentStore  
WHERE Name = N'document.docx';  
  
-- returns "\\MyServer\MSSQLSERVER\MyDocumentDatabase\MyFileTable\MyDocDirectory\document.docx"  
SELECT file_stream.GetFileNamespacePath(1, Null) AS FilePath FROM DocumentStore  
WHERE Name = N'document.docx';  
```  
  
## <a name="see-also"></a>関連項目  
 [FileTable 内のディレクトリとパスの操作](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
