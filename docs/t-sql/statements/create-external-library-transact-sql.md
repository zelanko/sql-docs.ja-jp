---
title: CREATE EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
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
- CREATE EXTERNAL LIBRARY
- CREATE_EXTERNAL_LIBRARY_TSQL
- EXTERNAL LIBRARY
- EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: e28716314837225586cf4bd1f80a37c5c6b824ab
ms.sourcegitcommit: 6e819406554efbd17bbf84cf210d8ebeddcf772d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="create-external-library-transact-sql"></a>CREATE EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]  

指定したバイト ストリームまたはファイル パスから R パッケージをデータベースにアップロードします。

このステートメントは、データベース管理者が新しい外部言語ランタイム (R、Python、Java など) に必要な成果物および [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] でサポートされる OS プラットフォームをアップロードするための汎用メカニズムとして機能します。 

現在、R 言語と Windows プラットフォームのみがサポートされています。 Python および Linux は、今後のリリースでサポートされる予定です。

## <a name="syntax"></a>構文

```text
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

ライブラリは、ユーザーを対象としたデータベースに追加されます。 つまり、ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされます。また、ライブラリ名はユーザーごとに一意である必要があります。 たとえば、**RUser1** と **RUser2** の 2 人のユーザーは、どちらも個別に R ライブラリ `ggplot2` をアップロードできます。

ライブラリ名は任意に割り当てることはできません。ライブラリ名は R から R ライブラリを読み込むために必要な名前と同じにする必要があります。

**owner_name**

外部ライブラリを所有しているユーザーまたはロールの名前を指定します。 このオプションを指定しない場合は、所有権は現在のユーザーに与えられます。

データベース所有者が所有するライブラリは、データベースとランタイムに対してグローバルと見なされます。 つまり、データベース所有者は、多くのユーザーによって共有されているライブラリまたはパッケージの共通セットが含まれているライブラリを作成できます。 `dbo` ユーザー以外のユーザーによって外部ライブラリが作成されると、その外部ライブラリは、そのユーザーに対してのみプライベートになります。

ユーザー **RUser1** が R スクリプトを実行するときに、`libPath` の値に複数のパスを含めることができます。 最初のパスは常に、データベースの所有者によって作成された共有のライブラリへのパスになります。 `libPath` の 2 番目の部分では、**RUser1** によって個別にアップロードされたパッケージを含むパスを指定します。

**file_spec**

特定のプラットフォーム用のパッケージのコンテンツを指定します。 プラットフォームごとに 1 つのファイル成果物のみがサポートされます。

ファイルは、ローカル パスまたはネットワーク パスの形式で指定することができます。

必要に応じて、ファイルの OS プラットフォームを指定できます。 特定の言語またはランタイムの OS プラットフォームごとに 1 つのファイル成果物またはコンテンツのみが許可されます。

**library_bits**

アセンブリと同様に、パッケージのコンテンツを 16 進数のリテラルとして指定します。 

このオプションは、ライブラリを作成または既存のライブラリを変更する (およびそれを行うために必要なアクセス許可を持つ) 必要があるが、サーバー上のファイル システムが制限されていて、サーバーがアクセスできる場所にライブラリ ファイルをコピーできない場合に役立ちます。

**PLATFORM = WINDOWS**

ライブラリのコンテンツのプラットフォームを指定します。 既定値は、SQL Server が実行されているホスト プラットフォームに設定されます。 そのため、ユーザーが値を指定する必要はありません。 複数のプラットフォームがサポートされている場合、またはユーザーが別のプラットフォームを指定する必要がある場合に必要です。 

SQL Server 2017 では、サポートされているプラットフォームは Windows のみです。

## <a name="remarks"></a>Remarks

R 言語の場合、ファイルを使用するときに、Windows の .ZIP 拡張子を使用して、ZIP アーカイブ ファイルの形式でパッケージを準備する必要があります。 現時点では、Windows プラットフォームのみがサポートされています。 

`CREATE EXTERNAL LIBRARY` ステートメントは、ライブラリ ビットをデータベースにアップロードします。 ユーザーが [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) を使用して外部スクリプトを実行し、パッケージまたはライブラリを呼び出すと、ライブラリがインストールされます。

インスタンスにアップロードされたライブラリは、パブリックまたはプライベートのいずれかにすることができます。 `dbo` のメンバーによってライブラリが作成された場合、そのライブラリはパブリックで、すべてのユーザーと共有することができます。 それ以外の場合、ライブラリはそのユーザーのみのプライベートになります。

SQL Server 2017 リリースでは、BLOB をデータ ソースとして使用することはできません。

## <a name="permissions"></a>アクセス許可

`CREATE ANY EXTERNAL LIBRARY` アクセス許可が必要です。

ライブラリを変更するには、別のアクセス許可 `ALTER ANY EXTERNAL LIBRARY` が必要です。

## <a name="examples"></a>使用例

### <a name="a-add-an-external-library-to-a-database"></a>A. 外部ライブラリをデータベースに追加する  

次の例では、`customPackage` と呼ばれる外部ライブラリをデータベースに追加します。

```sql
CREATE EXTERNAL LIBRARY customPackage
FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip') WITH (LANGUAGE = 'R');
```  

ライブラリがインスタンスに正常にアップロードされたら、ユーザーが `sp_execute_external_script` プロシージャを実行して、ライブラリをインストールします。

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'library(customPackage)'
```

### <a name="b-installing-packages-with-dependencies"></a>B. 依存関係を持つパッケージをインストールする

インストールするパッケージに依存関係がある場合は、ターゲットのパッケージをインストールする_前に_、最 1 レベルと第 2 レベルの両方の依存関係を分析し、必要なすべてのパッケージが利用できることを確認することが非常に重要です。

たとえば、新しいパッケージ `packageA` をインストールするとします。

+ `packageA` は `packageB` に依存関係があります
+ `packageB` は `packageC` に依存関係があります

`packageA` を正常にインストールするには、`packageA` を SQL Server に追加するのと同時に、`packageB` と `packageC` 用のライブラリを作成する必要があります。 必要なパッケージのバージョンも必ず確認してください。

実際には、一般的なパッケージのパッケージの依存関係は、通常、この単純な例よりもはるかに複雑です。 たとえば、ggplot2 には 30 を超えるパッケージが必要で、それらのパッケージには、サーバーで入手できない追加のパッケージが必要な場合があります。 パッケージが不足していたり、パッケージのバージョンが違っていたりすると、インストールが失敗する可能性があります。

パッケージ マニフェストを見ただけでは、すべての依存関係を判断するのは難しいため、[miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) や [iGraph](http://igraph.org/redirect.html) などのパッケージを使用して、インストールを正常に完了させるために必要なすべてのパッケージを特定することをお勧めします。

+ ターゲット パッケージとその依存関係をアップロードします。 すべてのファイルは、サーバーからアクセスできるフォルダー内にある必要があります。

    ```sql
    CREATE EXTERNAL LIBRARY packageA 
    FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageA.zip') 
    WITH (LANGUAGE = 'R'); 
    GO

    CREATE EXTERNAL LIBRARY packageB FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageB.zip') 
    WITH (LANGUAGE = 'R');
    GO

    CREATE EXTERNAL LIBRARY packageC FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageC.zip') 
    WITH (LANGUAGE = 'R');
    GO
    ```

+ 最初に必要なパッケージをインストールします。

    必要なパッケージが既にインスタンスにアップロードされている場合、もう一度追加する必要はありません。 既存のパッケージのバージョンが正しいことだけを確認してください。 
    
    `sp_execute_external_script` を最初に実行してパッケージ `packageA` をインストールすると、必要なパッケージ `packageC` と `packageB` が正しい順序でインストールされます。

    ただし、必要なパッケージが使用できない場合、ターゲット パッケージ `packageA` のインストールが失敗します。

    ```sql
    EXEC sp_execute_external_script 
    @language =N'R', 
    @script=N'
    # load the desired package packageA
    library(packageA)
    # call function from package
    OutputDataSet <- packageA.function()
    '
    with result sets (([result] int));    
    ```

### <a name="c-create-a-library-from-a-byte-stream"></a>C. バイト ストリームからライブラリを作成する

パッケージ ファイルをサーバー上の場所に保存できない場合は、パッケージのコンテンツを変数で渡すこともできます。 次の例では、ビットを 16 進数リテラルとして渡すことで、ライブラリを作成します。

```SQL
CREATE EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

ここでは読みやすくするために、16 進数の値が切り詰められています。

### <a name="d-change-an-existing-package-library"></a>D. 既存のパッケージ ライブラリを変更する

`ALTER EXTERNAL LIBRARY` DDL ステートメントは、新しいライブラリのコンテンツを追加または既存のライブラリのコンテンツを変更するために使用できます。 既存のライブラリを変更するには、`ALTER ANY EXTERNAL LIBRARY` アクセス許可が必要です。

詳細については、「[ALTER EXTERNAL LIBRARY](alter-external-library-transact-sql.md)」を参照してください。

### <a name="e-delete-a-package-library"></a>E. パッケージ ライブラリを削除する

データベースからパッケージ ライブラリを削除するには、ステートメントを実行します。

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

> [!NOTE]
> [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] の他の `DROP` ステートメントとは異なり、このステートメントは、ユーザーの権限を指定する省略可能なパラメーターをサポートしています。 このオプションは、所有権ロールを持つユーザーに、通常のユーザーによってアップロードされたライブラリを削除することを許可します。

## <a name="see-also"></a>参照

[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  
