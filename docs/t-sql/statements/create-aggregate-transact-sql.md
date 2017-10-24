---
title: "集計 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_AGGREGATE_TSQL
- CREATE AGGREGATE
- AGGREGATE_TSQL
- AGGREGATE
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE AGGREGATE statement
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: 62eebc19-9f15-4245-94fa-b3fcd64a9d42
caps.latest.revision: 50
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad5cf36e97bf3903cc9d42ec5179de6375624f95
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-aggregate-transact-sql"></a>CREATE AGGREGATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] のアセンブリのクラスで実装が定義される、ユーザー定義集計関数を作成します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]その実装に集計関数をバインドする、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]のインスタンスに、実装が含まれているアセンブリをアップロードする必要があります最初[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CREATE ASSEMBLY ステートメントを使用しています。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE AGGREGATE [ schema_name . ] aggregate_name  
        (@param_name <input_sqltype>   
        [ ,...n ] )  
RETURNS <return_sqltype>  
EXTERNAL NAME assembly_name [ .class_name ]  
  
<input_sqltype> ::=  
        system_scalar_type | { [ udt_schema_name. ] udt_type_name }  
  
<return_sqltype> ::=  
        system_scalar_type | { [ udt_schema_name. ] udt_type_name }  
  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 ユーザー定義集計関数が所属しているスキーマの名前です。  
  
 *aggregate_name*  
 作成する集計関数の名前です。  
  
 **@***param_name*  
 ユーザー定義集計で定義された 1 つまたは複数のパラメーター。 パラメーターの値は、集計関数の実行時にユーザーが指定する必要があります。 「アット」マークを使用して、パラメーター名を指定 (**@**) 最初の文字として。 パラメーター名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 パラメーターは関数に対してローカルです。  
  
 *system_scalar_type*  
 入力パラメーターの値または戻り値を保持する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムのスカラーのデータ型です。 すべてのスカラー データ型できますをパラメーターとして except に使用するユーザー定義集計**テキスト**、 **ntext**、および**イメージ**です。 などの非スカラー値型**カーソル**と**テーブル**を指定することはできません。  
  
 *udt_schema_name*  
 CLR ユーザー定義型が所属しているスキーマの名前です。 指定されていない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]参照*udt_type_name*次の順序で。  
  
-   ネイティブ SQL 型の名前空間  
  
-   現在のデータベースにおける現在のユーザーの既定のスキーマ  
  
-   現在のデータベースの **dbo** スキーマ。  
  
 *udt_type_name*  
 現在のデータベースに既に作成されている CLR ユーザー定義型の名前です。 場合*udt_schema_name*が指定されていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型が現在のユーザーのスキーマに属していると仮定します。  
  
 *アセンブリ名*[ **.***class_name* ]  
 ユーザー定義集計関数にバインドするアセンブリ、および必要に応じて、アセンブリが所属するスキーマの名前とユーザー定義集計を実装するアセンブリ内のクラス名を指定します。 アセンブリは、CREATE ASSEMBLY ステートメントを使用してデータベース内に作成されている必要があります。 *class_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子と一致するアセンブリ内に存在するクラスの名前。 *class_name*クラスの記述に使用するプログラミング言語は、c# などの名前空間を使用している場合、名前空間で修飾された名前があります。 場合*class_name*が指定されていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と同じであると仮定*aggregate_name*です。  
  
## <a name="remarks"></a>解説  
 既定では、CLR コードを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能はオフになっています。 インスタンスでこれらのモジュール内のコードは実行できませんが、作成、変更、およびマネージ コード モジュールを参照するデータベース オブジェクトを削除することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しない限り、 [clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)を使用して有効になっているは[sp _構成](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
 参照されるアセンブリのクラス*assembly_name* 、そのメソッドのインスタンスで、ユーザー定義集計関数を実装するためのすべての要件を満たす必要がありますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。 [clr ユーザー定義集計](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)です。  
  
## <a name="permissions"></a>Permissions  
 EXTERNAL NAME 句で指定されているアセンブリ上に CREATE AGGREGATE 権限と REFERENCES 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、StringUtilities.csproj サンプル アプリケーションがコンパイルされていることを前提としています。 詳細については、次を参照してください。[文字列ユーティリティ関数サンプル](http://msdn.microsoft.com/library/9623013f-15f1-4614-8dac-1155e57c880c)です。  
  
 この例は集計 `Concatenate` を作成します。 集計が作成される前に、アセンブリ`StringUtilities.dll`がローカル データベースに登録します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
-- You may have to modify the value of the this variable if you have  
--installed the sample some location other than the default location.  
  
SELECT @SamplesPath = REPLACE(physical_name, 'Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\master.mdf', 'Microsoft SQL Server\130\Samples\Engine\Programmability\CLR\')   
     FROM master.sys.database_files   
     WHERE name = 'master';  
  
CREATE ASSEMBLY StringUtilities FROM @SamplesPath + 'StringUtilities\CS\StringUtilities\bin\debug\StringUtilities.dll'  
WITH PERMISSION_SET=SAFE;  
GO  
  
CREATE AGGREGATE Concatenate(@input nvarchar(4000))  
RETURNS nvarchar(4000)  
EXTERNAL NAME [StringUtilities].[Microsoft.Samples.SqlServer.Concatenate];  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DROP AGGREGATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-aggregate-transact-sql.md)  
  
  

