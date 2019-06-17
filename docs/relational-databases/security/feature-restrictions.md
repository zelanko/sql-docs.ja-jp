---
title: 機能の制限 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: vainolo
ms.author: arib
manager: tomerw
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 99a0a768334ab5335591fae69e4f18060fba9866
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66506920"
---
# <a name="feature-restrictions"></a>機能の制限

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server 攻撃の一般的な原因の 1 つがデータベースにアクセスする Web アプリケーションです。さまざまな形式の SQL インジェクション攻撃が使用され、データベースに関する情報が少しずつ収集されます。  理論上、SQL インジェクションを許さないようにアプリケーション コードは開発されます。  しかしながら、古い外部のコードが含まれる大規模なコードベースでは、すべてに対処しているとは誰も確信できず、現実として、SQL インジェクションからシステムを守らなければなりません。  機能の制限の目標は、何らかの形式の SQL インジェクションを許したとしても、それによるデータベースの情報漏洩を防ぐことにあります。

## <a name="enabling-feature-restrictions"></a>機能の制限を有効にする

機能の制限は、次のように `sp_add_feature_restriction` ストアド プロシージャを利用して有効化されます。

```sql
EXEC sp_add_feature_restriction <feature>, <object_class>, <object_name>
```

制限できる機能:

| 機能          | [説明] |
|------------------|-------------|
| N'ErrorMessages' | 制限されると、エラー メッセージ内のユーザー データにマスキングが適用されます。 「[エラー メッセージの機能の制限](#error-messages-feature-restriction)」をご覧ください。 |
| N'Waitfor'       | 制限されると、コマンドは遅延なく直後に返されます。 「[WAITFOR の機能の制限](#waitfor-feature-restriction)」を参照してください。 |

`object_class` の値は `N'User'` または `N'Role'` であり、データベースで `object_name` がユーザー名であるか、ロール名であるかを示します。

次の例では、ユーザー `MyUser` のすべてのエラー メッセージにマスキングが適用されます。

```sql
EXEC sp_add_feature_restriction N'ErrorMessages', N'User', N'MyUser'
```

## <a name="disabling-feature-restrictions"></a>機能の制限を無効にする

機能の制限は、次のように `sp_drop_feature_restriction` ストアド プロシージャを利用して無効化されます。

```sql
EXEC sp_drop_feature_restriction <feature>, <object_class>, <object_name>
```

次の例では、ユーザー `MyUser` のエラー メッセージのマスキングが無効になります。

```sql
EXEC sp_drop_feature_restriction N'ErrorMessages', N'User', N'MyUser'
```

## <a name="viewing-feature-restrictions"></a>機能の制限を表示する

`sys.sql_feature_restrictions` ビューには、データベースで現在定義されているすべての機能制限が表示されます。 詳細は、「[sys.sql_feature_restrictions](../system-catalog-views/sys-sql-feature-restrictions.md)」を参照してください。

## <a name="feature-restrictions"></a>機能の制限

### <a name="error-messages-feature-restriction"></a>エラー メッセージの機能の制限

SQL インジェクション攻撃の一般的な手法の 1 つが、エラーを引き起こすコードを挿入することです。  エラー メッセージを調べることで、攻撃者はシステムに関する情報を知り、さらに攻撃対象を絞ってさらなる攻撃を仕掛けることができます。  この攻撃は、アプリケーションでクエリの結果が表示されないが、エラー メッセージを表示するとき、特に効果的です。

ある Web アプリケーションに次の形式の要求があるとします。

```html
http://www.contoso.com/employee.php?id=1
```

これにより次のデータベース クエリが実行されます。

```sql
SELECT Name FROM EMPLOYEES WHERE Id=$EmpId
```

Web アプリケーション要求に `Id` パラメーターとして渡される値がコピーされ、データベース クエリの $EmpId が置換された場合、攻撃者は次の要求を行うことができます。

```html
http://www.contoso.com/employee.php?id=1 AND CAST(DB_NAME() AS INT)=0
```

また、次のエラーが返され、攻撃者がデータベースの名前を知ることを許します。

```sql
Conversion failed when converting the nvarchar value 'HR_Data' to data type int.
```

データベースのアプリケーション ユーザーに対してエラー メッセージの機能制限を有効にすると、返されるエラー メッセージにマスキングが適用され、データベースに関する内部情報が漏れなくなります。

```sql
Conversion failed when converting the ****** value '******' to data type ******.
```

同様に、攻撃者は次の要求を行うことができます。

```html
http://www.contoso.com/employee.php?id=1 AND CAST(Salary AS TINYINT)=0
```

また、次のエラーが返され、攻撃者が従業員の給与を知ることを許します。

```sql
Arithmetic overflow error for data type tinyint, value = 140000.
```

エラー メッセージの機能制限を使用することで、データベースから次が返されます。

```sql
Arithmetic overflow error for data type ******, value = ******.
```

### <a name="waitfor-feature-restriction"></a>WAITFOR の機能の制限

挿入された SQL の結果やエラー メッセージがアプリケーションから攻撃者に与えられなくても、2 つの条件分岐で実行時間が異なる条件付きクエリを構築することで、攻撃者はデータベースの情報を推測できることがあります。それがブラインド SQL インジェクションです。 応答時間を比較することで、攻撃者は実行された分岐を知り、やがてはシステムに関する情報を得るに至ります。 この攻撃の最も単純な形態は、`WAITFOR` ステートメントを利用して遅延を生み出すことです。

ある Web アプリケーションに次の形式の要求があるとします。

```html
http://www.contoso.com/employee.php?id=1
```

これにより次のデータベース クエリが実行されます。

```sql
SELECT Name FROM EMPLOYEES WHERE Id=$EmpId
```

Web アプリケーション要求に `Id` パラメーターとして渡される値がコピーされ、データベース クエリの $EmpId が置換された場合、攻撃者は次の要求を行うことができます。

```html
http://www.contoso.com/employee.php?id=1; IF SYSTEM_USER='sa' WAITFOR DELAY '00:00:05'
```

また、`sa` アカウントが使用される場合、クエリに追加で 5 秒かかります。 `WAITFOR` 機能制限がデータベースで無効になっている場合、`WAITFOR` ステートメントは無視され、この攻撃で情報が漏洩することはありません。
