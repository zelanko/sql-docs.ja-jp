---
title: CREATE EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: HeidiSteen
ms.author: heidist
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9b03dd4e3e18a9e67bcdf07c867d0ddb93c19a73
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "40409403"
---
# <a name="create-external-library-transact-sql"></a>CREATE EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]  

指定したバイト ストリームまたはファイル パスから R パッケージをデータベースにアップロードします。

このステートメントは、データベース管理者が新しい外部言語ランタイム (R、Python、Java など) に必要な成果物および [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] でサポートされる OS プラットフォームをアップロードするための汎用メカニズムとして機能します。 

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

ライブラリは、ユーザーを対象としたデータベースに追加されます。 ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされる必要があります。 たとえば、**RUser1** と **RUser2** の 2 人のユーザーは、どちらも個別に R ライブラリ `ggplot2` をアップロードできます。 ただし、**RUser1** が新しいバージョンの `ggplot2` をアップロードする場合は、2 番目のインスタンスの名前を別のものにするか、既存のライブラリを置き換える必要があります。 

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

## <a name="permissions"></a>アクセス許可

`CREATE EXTERNAL LIBRARY` アクセス許可が必要です。 既定では、**db_owner** ロールのメンバーである **dbo** を持つすべてのユーザーに、外部ライブラリを作成する権限があります。 その他のすべてのユーザーには、特権として CREATE EXTERNAL LIBRARY を指定して、[GRANT](https://docs.microsoft.com/sql/t-sql/statements/grant-database-permissions-transact-sql) ステートメントを使用する権限を明示的に付与する必要があります。

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

実際には、一般的なパッケージのパッケージの依存関係は、通常、この単純な例よりもはるかに複雑です。 たとえば、**ggplot2** には 30 を超えるパッケージが必要で、それらのパッケージには、サーバーで入手できない追加のパッケージが必要な場合があります。 パッケージが不足していたり、パッケージのバージョンが違っていたりすると、インストールが失敗する可能性があります。

パッケージ マニフェストを見ただけでは、すべての依存関係を判断するのは難しいため、[miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) などのパッケージを使用して、インストールを正常に完了させるために必要なすべてのパッケージを特定することをお勧めします。

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
    print(packageVersion("packageA"))
    '
    ```

### <a name="c-create-a-library-from-a-byte-stream"></a>C. バイト ストリームからライブラリを作成する

パッケージ ファイルをサーバー上の場所に保存できない場合は、パッケージのコンテンツを変数で渡すことができます。 次の例では、ビットを 16 進数リテラルとして渡すことで、ライブラリを作成します。

```SQL
CREATE EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

> [!NOTE]
> このコード サンプルは構文のみを示しています。`CONTENT =` のバイナリ値は読みやすさのため切り捨てられており、作業ライブラリを作成しません。 バイナリ変数の実際の内容はこれよりも長くなります。

### <a name="d-change-an-existing-package-library"></a>D. 既存のパッケージ ライブラリを変更する

`ALTER EXTERNAL LIBRARY` DDL ステートメントは、新しいライブラリのコンテンツを追加または既存のライブラリのコンテンツを変更するために使用できます。 既存のライブラリを変更するには、`ALTER ANY EXTERNAL LIBRARY` アクセス許可が必要です。

詳細については、「[ALTER EXTERNAL LIBRARY](alter-external-library-transact-sql.md)」を参照してください。

## <a name="see-also"></a>参照

[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  
