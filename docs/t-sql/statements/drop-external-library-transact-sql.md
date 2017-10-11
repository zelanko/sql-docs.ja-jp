---
title: "外部ライブラリ (TRANSACT-SQL) の削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: ac2814f7c0b0d1bf6de60d52ea65e54caab0f72d
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="drop-external-library-transact-sql"></a>ドロップ外部ライブラリ (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

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


