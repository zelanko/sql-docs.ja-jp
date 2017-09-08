---
title: "外部ライブラリ (TRANSACT-SQL) を ALTER |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 541419770828e01cca82fb33ead1b22170f8e4f3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-external-library-transact-sql"></a>ALTER 外部ライブラリ (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

既存のライブラリのコンテンツを変更します。  

## <a name="syntax"></a>構文

```
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = 'R' )
[ ; ]

<file_spec> ::=
{
(CONTENT = { <client_library_specifier> | <library_bits> | NONE}
[, PLATFORM = WINDOWS )
}

<client_library_specifier> :: =
  '[\\computer_name\]share_name\[path\]manifest_file_name'
| '[local_path\]manifest_file_name'
| '<relative_path_in_external_data_source>'

<library_bits> :: =
{ varbinary_literal | varbinary_expression }
```

### <a name="arguments"></a>引数

**library_name**

既存のパッケージ ライブラリの名前を指定します。 ライブラリは、ユーザーにスコープされます。 つまり、ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされます。

**owner_name**

ユーザーまたは外部のライブラリを所有しているロールの名前を指定します。

**file_spec**

特定のプラットフォーム用のパッケージのコンテンツを指定します。 プラットフォームごとの 1 つのファイルの成果物はサポートされています。

ファイルは、ローカル パスまたはネットワーク パスの形式で指定することができます。 ファイル名で参照されているコンテナーに対する相対パスを指定できますデータ ソースのオプションが指定されている場合、`EXTERNAL DATA SOURCE`です。

必要に応じて、ファイルの OS プラットフォームを指定できます。 1 ファイルのみの成果物またはコンテンツについては、特定の言語や実行時の OS プラットフォームごとに許可します。

**DATA_SOURCE external_data_source_name を =**

ライブラリ ファイルの場所を含む外部データ ソースの名前を指定します。 この場所は、Azure blob ストレージ パスを参照する必要があります。 外部データ ソースを作成するには、使用[外部データ ソースの作成 (TRANSACT-SQL)](create-external-data-source-transact-sql.md)です。

**プラットフォーム WINDOWS を =**

コンテンツ ライブラリのプラットフォームを指定します。 この値は、さまざまなプラットフォームを追加する既存のライブラリを変更する場合に必要です。 Windows は、唯一サポートされているプラットフォームです。

## <a name="remarks"></a>解説

R 言語用には、zip 形式のアーカイブ ファイルの形式でパッケージを準備します。Windows の ZIP 拡張子です。 現時点では、Windows プラットフォームのみがサポートされています。  
`ALTER EXTERNAL LIBRARY`ステートメントがデータベースにのみライブラリ ビットをアップロードします。 変更したライブラリが実際にインストールされていないユーザーが実行されるまで外部のスクリプトは、その後を実行して[sp_execute_external_script (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

## <a name="permissions"></a>Permissions
必要があります、`ALTER ANY EXTERNAL LIBRARY`権限です。 外部のライブラリを作成したユーザーは、その外部のライブラリを変更できます。

## <a name="examples"></a>使用例

次の例では、customPackage と呼ばれる外部ライブラリを変更します。

```sql  
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  
実行し、`sp_execute_external_script`手順、ライブラリをインストールします。

```sql   
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)

# call customPackageFunc
OutputDataSet <- customPackageFunc()
'
with result sets (([result] int));    
```


## <a name="see-also"></a>参照  
[外部ライブラリ (TRANSACT-SQL) を作成する](create-external-library-transact-sql.md)
[(TRANSACT-SQL) の外部ライブラリの削除](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

