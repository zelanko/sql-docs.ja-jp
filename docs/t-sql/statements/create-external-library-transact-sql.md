---
title: "外部ライブラリ (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0f11a6b7633be392e1f789e12c43f2e5d6e56b47
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-library-transact-sql"></a>外部ライブラリ (TRANSACT-SQL) を作成します。  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

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

**プラットフォーム WINDOWS を =**

コンテンツ ライブラリのプラットフォームを指定します。 SQL Server が実行されているホスト プラットフォームの既定値。 そのため、ユーザーは、値を指定がありません。 複数のプラットフォームがサポートされている場合、またはユーザーが別のプラットフォームを指定する必要がある場合に必要です。 Windows は、唯一サポートされているプラットフォームです。

## <a name="remarks"></a>解説

R 言語用には、zip 形式のアーカイブ ファイルの形式でパッケージを準備します。Windows の ZIP 拡張子です。 現時点では、Windows プラットフォームのみがサポートされています。  

`CREATE EXTERNAL LIBRARY`ステートメントがデータベースにのみライブラリ ビットをアップロードします。 ライブラリが実際にインストールされていないユーザーが実行されるまで外部のスクリプトは、その後を実行して[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。  

## <a name="permissions"></a>Permissions  
必要があります、`CREATE EXTERNAL LIBRARY`権限です。  

## <a name="examples"></a>使用例

### <a name="a-add-an-external-library-to-a-database"></a>A. 外部ライブラリ データベースに追加します。  
次の例では、データベースに customPackage と呼ばれる外部ライブラリを追加します。   
```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 
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

### <a name="b-installing-packages-with-dependencies"></a>B. 依存関係を持つパッケージをインストールします。

場合`packageB`に依存している`packageA`、そのコードは、このような一般的なプリンシパルを例に従います。   
```
CREATE EXTERNAL LIBRARY packageA 
FROM 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\ggplot2.zip') 
WITH (LANGUAGE = 'R'); 

CREATE EXTERNAL LIBRARY packageB FROM 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\ggplot2.zip') 
WITH (LANGUAGE = 'R');
```

`packageA`および`packageB`はどちらもインストール時に`sp_execute_external_script`が最初に実行します。   
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

これを行うには、パッケージが保存されているフォルダーをサーバーにアクセスする必要があります。 

### <a name="change-an-existing-package-library"></a>既存のパッケージ ライブラリを変更します。

`ALTER EXTERNAL LIBRARY` DDL ステートメントは、新しいライブラリのコンテンツを追加または既存のライブラリのコンテンツを変更するために使用できます。   

### <a name="delete-a-package-library"></a>パッケージのライブラリを削除します。

データベースからパッケージ ライブラリを削除するには、ステートメントを実行します。

```sql
DROP EXTERNAL LIBRARY ggplot2 <user_name>;
```

> [!NOTE]
> その他のとは異なり`DROP`内のステートメント[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]、このステートメントは、ユーザーの権限を指定する省略可能なパラメーターをサポートしています。 このオプションでは、通常のユーザーによってアップロードされたライブラリを削除する、ロールの所有権できます。 

## <a name="see-also"></a>参照  
[ALTER 外部ライブラリ (TRANSACT-SQL)](alter-external-library-transact-sql.md)  
[ドロップ外部ライブラリ (TRANSACT-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

