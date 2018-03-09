---
title: "外部ライブラリ (TRANSACT-SQL) の削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: 8c45da28bf795fca50454fde21eb7d2c3c798296
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="drop-external-library-transact-sql"></a>ドロップ外部ライブラリ (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

既存のパッケージ ライブラリを削除します。

## <a name="syntax"></a>構文  

```
DROP EXTERNAL LIBRARY library_name  
[ AUTHORIZATION owner_name ];  
```

### <a name="arguments"></a>引数

**library_name**

既存のパッケージ ライブラリの名前を指定します。

ライブラリは、ユーザーにスコープされます。 つまり、ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされます。

**owner_name**

ユーザーまたは外部のライブラリを所有しているロールの名前を指定します。

データベース所有者は、その他のユーザーによって作成されたライブラリを削除できます。

### <a name="return-values"></a>戻り値

ステートメントが成功した場合は、情報メッセージが返されます。

## <a name="remarks"></a>解説

その他のとは異なり`DROP`SQL Server でのステートメント、このステートメントをサポートしている省略可能な承認句を指定します。 これにより、 **dbo**またはユーザーに、 **db_owner**データベース内の正規のユーザーによってアップロードされたパッケージ ライブラリを削除するロール。

## <a name="examples"></a>使用例

という名前でカスタムの R パッケージを追加`customPackage`データベースにします。

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 'C:\Users\Username\CustomPackages\customPackage.zip';
```

削除、`customPackage`ライブラリです。

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

## <a name="see-also"></a>参照  
[外部ライブラリ (TRANSACT-SQL) を作成します。](create-external-library-transact-sql.md)  
[ALTER 外部ライブラリ (TRANSACT-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

