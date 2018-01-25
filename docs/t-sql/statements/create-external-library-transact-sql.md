---
title: "外部ライブラリ (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/05/2017
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
- CREATE EXTERNAL LIBRARY
- CREATE_EXTERNAL_LIBRARY_TSQL
- EXTERNAL LIBRARY
- EXTERNAL_LIBRARY_TSQL
dev_langs: TSQL
helpviewer_keywords: CREATE EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: fe1cb90bce5717d194defd2c684d7b20fc29a061
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="create-external-library-transact-sql"></a>外部ライブラリ (TRANSACT-SQL) を作成します。  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]  

指定したバイトのストリームまたはファイルのパスからデータベースへの R パッケージをアップロードします。

このステートメントは、データベース管理者 (R、Python、Java など) は、新しい外部の言語ランタイムの必要な成果物およびによってサポートされる OS プラットフォームをアップロードするための一般的なメカニズムとして機能[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]します。 現在、R 言語のみと Windows プラットフォームがサポートされます。

## <a name="syntax"></a>構文

```
CREATE EXTERNAL LIBRARY library_name  
    [ AUTHORIZATION owner_name ]  
FROM <file_spec> [,…2]  
WITH ( LANGUAGE = 'R' )  
[ ; ]  

<file_spec> ::=  
{  
(CONTENT = { <client_library_specifier> | <library_bits> }  
[, PLATFORM = WINDOWS ])  
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

ライブラリは、データベースのユーザーにスコープに追加されます。 つまり、ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされます、ライブラリ名は、ユーザーごとに一意である必要があります。 たとえば、2 人のユーザー **RUser1**と**RUser2**両方個別に、個別にアップロードできる、R ライブラリ`ggplot2`です。

**owner_name**

ユーザーまたは外部のライブラリを所有しているロールの名前を指定します。 このオプションを指定しない場合は、所有権は現在のユーザーに与えられます。

データベース所有者が所有するライブラリは、データベースと実行時にグローバルと見なされます。 つまり、データベース所有者は、ライブラリまたは多くのユーザーによって共有されているパッケージの共通セットが含まれているライブラリを作成できます。 作成時に外部ライブラリのユーザー以外の場合、`dbo`ユーザー、外部ライブラリは、そのユーザーのみにプライベートです。

ときに、ユーザー **RUser1**の値、R スクリプトを実行`libPath`複数のパスを含めることができます。 最初のパスは、データベースの所有者によって作成された共有のライブラリへのパスでは常にします。 2 番目の部分の`libPath`で個別にアップロードされたパッケージを含むパスを指定**RUser1**です。

**file_spec**

特定のプラットフォーム用のパッケージのコンテンツを指定します。 プラットフォームごとの 1 つのファイルの成果物はサポートされています。

ファイルは、ローカル パス、またはネットワーク パスの形式で指定することができます。

必要に応じて、ファイルの OS プラットフォームを指定できます。 1 ファイルのみの成果物またはコンテンツについては、特定の言語や実行時の OS プラットフォームごとに許可します。

**library_bits**

アセンブリのような 16 進数のリテラルとして、パッケージのコンテンツを指定します。 このオプションが必要なアクセス許可が、サーバーがアクセスできる任意のフォルダーにファイルのパスへのアクセスはありません、ライブラリを変更するライブラリを作成することができます。

**PLATFORM = WINDOWS**

コンテンツ ライブラリのプラットフォームを指定します。 SQL Server が実行されているホスト プラットフォームの既定値。 そのため、ユーザーは、値を指定がありません。 複数のプラットフォームがサポートされている場合、またはユーザーが別のプラットフォームを指定する必要がある場合に必要です。 Windows は、唯一サポートされているプラットフォームです。

## <a name="remarks"></a>解説

Zip アーカイブ ファイルの形式で、R 言語用、ファイルを使用するときに、パッケージを準備する必要があります、します。Windows の ZIP 拡張子です。 現時点では、Windows プラットフォームのみがサポートされています。

`CREATE EXTERNAL LIBRARY`ステートメントがデータベースにのみライブラリ ビットをアップロードします。 ライブラリが実際にインストールされていないユーザーが実行されるまで外部のスクリプトは、その後を実行して[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。  

インスタンスにアップロードされたライブラリには、public または private のいずれかを指定できます。 メンバーで、ライブラリが作成される場合`dbo`ライブラリはパブリックでは、すべてのユーザーと共有することができます。 それ以外の場合、ライブラリは、そのユーザーにしか専用です。

SQL Server 2017 リリースのデータ ソースとして blob を使用することはできません。

## <a name="permissions"></a>権限

必要があります、`CREATE ANY EXTERNAL LIBRARY`権限です。

ライブラリを変更するには、別個の権限が必要です`ALTER ANY EXTERNAL LIBRARY`です。

## <a name="examples"></a>使用例

### <a name="a-add-an-external-library-to-a-database"></a>A. 外部ライブラリ データベースに追加します。  

次の例では、データベースに customPackage と呼ばれる外部ライブラリを追加します。

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  

ユーザーが実行のインスタンスには、ライブラリを正常にアップロードされましたが、後に、`sp_execute_external_script`手順、ライブラリをインストールします。

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)
'
```

### <a name="b-installing-packages-with-dependencies"></a>B. 依存関係を持つパッケージをインストールします。

場合`packageB`に依存している`packageA`、次の一般原則に従います。

+ ターゲットのパッケージとその依存関係の両方をアップロードします。

    両方のパッケージは、サーバーにアクセスできるフォルダーでなければなりません。

    ```sql
    CREATE EXTERNAL LIBRARY packageA 
    FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageA.zip') 
    WITH (LANGUAGE = 'R'); 
    
    CREATE EXTERNAL LIBRARY packageB FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageB.zip') 
    WITH (LANGUAGE = 'R');
    ```

+ 依存関係は、最初にインストールされます。

    場合必要なパッケージ`packageA`既にアップロードされて、インスタンスに、必要がありますがインストールされていないとは別にします。 必要なパッケージ`packageA`ときでインストールされている`sp_execute_external_script`の最初のパッケージをインストールする実行`packageB`です。

    ただし場合、必要なパッケージ`packageA`、使用できない場合、対象パッケージのインストール`packageB`は失敗します。

    ```sql
    EXEC sp_execute_external_script 
    @language =N'R', 
    @script=N'
    # load packageB
    library(packageB)
    # call customPackageBFunc
    OutputDataSet <- customPackageBFunc()
    '
    with result sets (([result] int));    
    ```

### <a name="c-create-a-library-from-a-byte-stream"></a>C. バイト ストリームからライブラリを作成します。

次の例を渡すことによって、ライブラリを作成する 16 進数リテラルとしてビットを更新します。

```SQL
CREATE EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

### <a name="d-change-an-existing-package-library"></a>D. 既存のパッケージ ライブラリを変更します。

`ALTER EXTERNAL LIBRARY` DDL ステートメントは、新しいライブラリのコンテンツを追加または既存のライブラリのコンテンツを変更するために使用できます。 既存のライブラリを変更する必要があります、`ALTER ANY EXTERNAL LIBRARY`権限です。

詳細については、次を参照してください。[外部ライブラリの ALTER](alter-external-library-transact-sql.md)です。

### <a name="e-delete-a-package-library"></a>E. パッケージのライブラリを削除します。

データベースからパッケージ ライブラリを削除するには、ステートメントを実行します。

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

> [!NOTE]
> その他のとは異なり`DROP`内のステートメント[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]、このステートメントは、ユーザーの権限を指定する省略可能なパラメーターをサポートしています。 このオプションでは、通常のユーザーによってアップロードされたライブラリを削除する、ロールの所有権できます。

## <a name="see-also"></a>参照

[ALTER 外部ライブラリ (TRANSACT-SQL)](alter-external-library-transact-sql.md)  
[ドロップ外部ライブラリ (TRANSACT-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  
