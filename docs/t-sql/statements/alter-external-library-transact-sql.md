---
title: ALTER EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: HeidiSteen
ms.author: heidist
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fd521263853eee1d0c8c25eb135ff2d309eb4a75
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43100820"
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

既存のパッケージ ライブラリの名前を指定します。 ライブラリは、ユーザーに範囲指定されます。 ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされる必要があります。

ライブラリ名を任意に割り当てることはできません。 つまり、呼び出し元のランタイムがパッケージの読み込み時に想定している名前を使用する必要があります。

**owner_name**

外部ライブラリを所有しているユーザーまたはロールの名前を指定します。

**file_spec**

特定のプラットフォーム用のパッケージのコンテンツを指定します。 プラットフォームごとに 1 つのファイル成果物のみがサポートされます。

ファイルは、ローカル パスまたはネットワーク パスの形式で指定することができます。 データ ソース オプションが指定されている場合、ファイル名は `EXTERNAL DATA SOURCE` で参照されているコンテナーに対する相対パスにすることができます。

必要に応じて、ファイルの OS プラットフォームを指定できます。 特定の言語またはランタイムの OS プラットフォームごとに 1 つのファイル成果物またはコンテンツのみが許可されます。

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

既定では、**dbo** ユーザーまたはロール **db_owner** のすべてのメンバーが、ALTER EXTERNAL LIBRARY を実行する権限を持っています。 さらに、外部ライブラリを作成したユーザーも、その外部ライブラリを変更できます。

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
ALTER EXTERNAL LIBRARY customLibrary 
SET (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

> [!NOTE]
> このコード サンプルは構文のみを示しています。`CONTENT =` のバイナリ値は読みやすさのため切り捨てられており、作業ライブラリを作成しません。 バイナリ変数の実際の内容はこれよりも長くなります。

## <a name="see-also"></a>参照

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md) 
