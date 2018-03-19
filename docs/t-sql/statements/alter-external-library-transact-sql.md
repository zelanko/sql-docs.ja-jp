---
title: ALTER EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 02/25/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: 
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
manager: craigg
ms.openlocfilehash: 0581957db73b82b9486f938d17b4c8938e20258d
ms.sourcegitcommit: 6e819406554efbd17bbf84cf210d8ebeddcf772d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="alter-external-library-transact-sql"></a>ALTER EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

既存の外部パッケージ ライブラリのコンテンツを変更します。

## <a name="syntax"></a>構文

```text
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

既存のパッケージ ライブラリの名前を指定します。 ライブラリは、ユーザーに範囲指定されます。 つまり、ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされます。

ライブラリ名を任意に割り当てることはできません。 つまり、呼び出し元のランタイムがパッケージの読み込み時に想定している名前を使用する必要があります。

**owner_name**

外部ライブラリを所有しているユーザーまたはロールの名前を指定します。

**file_spec**

特定のプラットフォーム用のパッケージのコンテンツを指定します。 プラットフォームごとに 1 つのファイル成果物のみがサポートされます。

ファイルは、ローカル パスまたはネットワーク パスの形式で指定することができます。 データ ソース オプションが指定されている場合、ファイル名は `EXTERNAL DATA SOURCE` で参照されているコンテナーに対する相対パスにすることができます。

必要に応じて、ファイルの OS プラットフォームを指定できます。 特定の言語またはランタイムの OS プラットフォームごとに 1 つのファイル成果物またはコンテンツのみが許可されます。

**DATA_SOURCE = external_data_source_name**

ライブラリ ファイルの場所を含む外部データ ソースの名前を指定します。 この場所は、Azure Blob Storage パスを参照する必要があります。 外部データ ソースを作成するには、[CREATE EXTERNAL DATA SOURCE (Transact-SQL)](create-external-data-source-transact-sql.md) を使用します。

> [!IMPORTANT] 
> 現在、SQL Server 2017 リリースでは、BLOB はデータ ソースとしてサポートされていません。

**library_bits**

アセンブリと同様に、パッケージのコンテンツを 16 進数のリテラルとして指定します。 

このオプションは、ライブラリを変更するのにアクセス許可はあるが、サーバー上のファイルへのアクセスが制限されていて、サーバーがアクセスできるパスにコンテンツを保存できない場合に役に立ちます。

代わりに、パッケージのコンテンツを変数としてバイナリ形式で渡すことができます。

**PLATFORM = WINDOWS**

ライブラリのコンテンツのプラットフォームを指定します。 この値は、さまざまなプラットフォームを追加する既存のライブラリを変更する場合に必要です。 サポートされているプラットフォームは Windows のみです。

## <a name="remarks"></a>Remarks

R 言語の場合、Windows の .ZIP 拡張子を使用して、ZIP アーカイブ ファイルの形式でパッケージを準備する必要があります。 現時点では、Windows プラットフォームのみがサポートされています。  

`ALTER EXTERNAL LIBRARY` ステートメントは、ライブラリ ビットのデータベースへのアップロードのみを行います。 ユーザーがライブラリを呼び出す [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) でコードを実行すると、変更したライブラリがインストールされます。

## <a name="permissions"></a>アクセス許可

`ALTER ANY EXTERNAL LIBRARY` アクセス許可が必要です。 外部ライブラリを作成したユーザーは、その外部ライブラリを変更できます。

## <a name="examples"></a>使用例

次の例では、`customPackage` と呼ばれる外部ライブラリを変更します。

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. ファイルを使用してライブラリのコンテンツを置き換える

次の例では、更新されたビットを含む ZIP 形式のファイルを使用して、`customPackage` と呼ばれる外部ライブラリを変更します。

```sql
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```

更新されたライブラリをインストールするには、ストアド プロシージャ `sp_execute_external_script` を実行します。

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'library(customPackage)'
;
```

### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>B. バイト ストリームを使用して既存のライブラリを変更する

次の例では、新しいビットを 16 進数リテラルとして渡すことで、ライブラリを変更します。

```SQL
ALTER EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

このサンプル コードでは、読みやすくするため、変数のコンテンツが切り詰められています。

## <a name="see-also"></a>参照

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md) 
