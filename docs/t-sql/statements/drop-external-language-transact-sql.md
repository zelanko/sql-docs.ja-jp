---
title: DROP EXTERNAL LANGUAGE (Transact-SQL) - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2019
ms.prod: sql
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6f4b6ee38ed70da600ef007f168cd7e95a010278
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85766363"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

既存の外部言語を削除します。

## <a name="syntax"></a>構文

```text
DROP EXTERNAL LANGUAGE <language_name>
```

### <a name="arguments"></a>引数

**language_name**

言語は、データベース スコープのオブジェクトです。 言語名は、データベース内で一意であることが必要です。

## <a name="permissions"></a>アクセス許可

言語を削除するには、ALTER ANY EXTERNAL LANGUAGE の特権が必要です。 既定では、すべてのデータベース所有者またはオブジェクトの所有者も、外部言語を削除することができます。

> [!NOTE]
> 外部言語を削除する前に、その外部言語を参照している外部ライブラリを削除する必要があることに注意してください。

### <a name="return-values"></a>戻り値

ステートメントが成功した場合は、情報メッセージが返されます。

## <a name="remarks"></a>解説

外部言語を削除するには、その前に、指定した言語に対するすべての外部ライブラリを削除する必要があります。

## <a name="examples"></a>例

外部言語 **Java** を作成します。

```sql
CREATE EXTERNAL LANGUAGE Java 
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

外部言語を削除します。

```sql
DROP EXTERNAL LANGUAGE Java;
```

## <a name="see-also"></a>参照

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[ALTER EXTERNAL LANGUAGE (Transact-SQL)](alter-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  
