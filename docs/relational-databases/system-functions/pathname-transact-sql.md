---
title: パス名 (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- PathName_TSQL
- PathName
dev_langs:
- TSQL
helpviewer_keywords:
- PathName FILESTREAM [SQL Server]
ms.assetid: 6b95ad90-6c82-4a23-9294-a2adb74934a3
author: rothja
ms.author: jroth
ms.openlocfilehash: f79f9f94d56c900d879fce06646b401f735e0bd0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140577"
---
# <a name="pathname-transact-sql"></a>PathName (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  FILESTREAM バイナリ ラージ オブジェクト (BLOB) のパスを返します。 OpenSqlFilestream API では、このパスを使用して、アプリケーションは、Win32 Api を使用して BLOB データを操作に使用できるハンドルを返します。 PathName は読み取り専用です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
column_name.PathName ( @option [ , use_replica_computer_name ] )  
```  
  
## <a name="arguments"></a>引数  
 *column_name*  
 列の名前を指定する**varbinary (max)** FILESTREAM 列です。 *column_name*列名にする必要があります。 式を指定したり、CAST ステートメントまたは CONVERT ステートメントの結果を指定したりすることはできません。  
  
 またはその他のデータ型の列に対して PathName を要求する**varbinary (max)** columnthat には、クエリのコンパイル時エラーが発生する FILESTREAM ストレージ属性はありません。  
  
 *@option*  
 整数[式](../../t-sql/language-elements/expressions-transact-sql.md)パスのサーバー コンポーネントの書式設定方法を定義します。 *@option* 次の値のいずれかを指定できます。 既定値は 0 です。  
  
|値|説明|  
|-----------|-----------------|  
|0|サーバー名を BIOS 形式に変換して返します (例: `\\SERVERNAME\MSSQLSERVER\v1\Archive\dbo\Records\Chart\A73F19F7-38EA-4AB0-BB89-E6C545DBD3F9`)。|  
|1|たとえば、サーバー名を変換せずが返されます。 `\\ServerName\MSSQLSERVER\v1\Archive\dbo\Records\Chart\A73F1`|  
|2|たとえば、サーバーの完全なパスが返されます。 `\\ServerName.MyDomain.com\MSSQLSERVER\v1\Archive\dbo\Records\Chart\A73F19F7-38EA-4AB0-BB89-E6C545DBD3F9`|  
  
 *use_replica_computer_name*  
 Always On 可用性グループで、サーバー名を返される方法を定義するビット値。  
  
 データベースは、Always On 可用性グループには属していない、ときにこの引数の値は無視されます。 コンピューター名は常に、パスに使用します。  
  
 Always On 可用性データベースが属している場合にグループ化、しの値*use_replica_computer_name*の出力には、次の影響、 **PathName**関数。  
  
|値|説明|  
|-----------|-----------------|  
|指定されていません。|関数は、パスに仮想ネットワーク名 (VNN) を返します。|  
|0|関数は、パスに仮想ネットワーク名 (VNN) を返します。|  
|1|関数は、パス内のコンピューター名を返します。|  
  
## <a name="return-type"></a>戻り値の型  
 **nvarchar(max)**  
  
## <a name="return-value"></a>戻り値  
 返される値は完全修飾論理パスまたは BLOB の NETBIOS パスです。 パス名では、IP アドレスは返されません。 FILESTREAM BLOB が作成されていない場合は、NULL が返されます。  
  
## <a name="remarks"></a>コメント  
 ROWGUID 列は、PathName を呼び出すクエリの表示である必要があります。  
  
 FILESTREAM BLOB は、[!INCLUDE[tsql](../../includes/tsql-md.md)] でのみ作成できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-reading-the-path-for-a-filestream-blob"></a>A. FILESTREAM BLOB のパスを読み取る  
 次の例では、`PathName` を `nvarchar(max)` 変数に代入します。  
  
```sql  
DECLARE @PathName nvarchar(max);  
SET @PathName = (  
    SELECT TOP 1 photo.PathName()  
    FROM dbo.Customer  
    WHERE LastName = 'CustomerName'  
    );  
```  
  
### <a name="b-displaying-the-paths-for-filestream-blobs-in-a-table"></a>B. テーブルに FILESTREAM Blob のパスを表示します。  
 次の例では、作成し、次の 3 つの FILESTREAM Blob のパスが表示されます。  
  
```sql  
-- Create a FILESTREAM-enabled database.  
-- The c:\data directory must exist.  
CREATE DATABASE PathNameDB  
ON  
PRIMARY ( NAME = ArchX1,  
    FILENAME = 'c:\data\archdatP1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = ArchX3,  
    FILENAME = 'c:\data\filestreamP1')  
LOG ON  ( NAME = ArchlogX1,  
    FILENAME = 'c:\data\archlogP1.ldf');  
GO  
  
USE PathNameDB;  
GO  
  
-- Create a table, add some records, and  
-- create the associated FILESTREAM  
-- BLOB files.  
  
CREATE TABLE TABLE1  
    (  
        ID int,  
        RowGuidColumn UNIQUEIDENTIFIER  
                      NOT NULL UNIQUE ROWGUIDCOL,  
        FILESTREAMColumn varbinary(MAX) FILESTREAM  
    );  
GO  
  
INSERT INTO TABLE1 VALUES  
 (1, NEWID(), 0x00)  
,(2, NEWID(), 0x00)  
,(3, NEWID(), 0x00);  
GO  
  
SELECT FILESTREAMColumn.PathName() AS 'PathName' FROM TABLE1;  
  
--Results  
--PathName  
------------------------------------------------------------------------------------------------------------  
--\\SERVER\MSSQLSERVER\v1\PathNameExampleDB\dbo\TABLE1\FILESTREAMColumn\DD67C792-916E-4A76-8C8A-4A85DC5DB908  
--\\SERVER\MSSQLSERVER\v1\PathNameExampleDB\dbo\TABLE1\FILESTREAMColumn\2907122B-2560-4CB9-86DC-FBE7ABA1843B  
--\\SERVER\MSSQLSERVER\v1\PathNameExampleDB\dbo\TABLE1\FILESTREAMColumn\922BE0E0-CAB9-4403-90BF-945BD258E4BC  
--  
--(3 row(s) affected)  
GO  
  
--Drop the database to clean up.  
USE master;  
GO  
DROP DATABASE PathNameDB;  
```  
  
## <a name="see-also"></a>関連項目  
 [バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [GET_FILESTREAM_TRANSACTION_CONTEXT &#40;TRANSACT-SQL&#41;](../../t-sql/functions/get-filestream-transaction-context-transact-sql.md)   
 [OpenSqlFilestream による FILESTREAM データへのアクセス](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
  
