---
title: R と Python スクリプトの実行 - SQL Server Machine Learning Services のデータベース アクセス許可の付与
description: SQL Server Machine Learning Services で R と Python スクリプトの実行、データベース ユーザーのアクセス許可を付与する方法。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e24095b7ec5aafd3439a3d344123c0a7f9dae86d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962324"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>SQL Server Machine Learning サービスへのアクセス許可をユーザーに付与します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、どのユーザーに付与できます SQL Server Machine Learning サービスで外部のスクリプトを実行して、読み取り、書き込み、またはデータの定義のデータベースへの言語 (DDL) のアクセス許可を付与するアクセス許可について説明します。

詳細については、アクセス許可のセクションを参照してください。[機能拡張フレームワークのセキュリティの概要](../../advanced-analytics/concepts/security.md#permissions)します。

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>スクリプトを実行するためのアクセス許可

インストールした場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]して、自分で独自のインスタンスで R または Python スクリプトの実行は、通常、管理者としてスクリプトを実行します。 したがって、さまざまな操作と、データベース内のすべてのデータに対する暗黙的なアクセス許可があります。

ただし、ほとんどのユーザーは、このような高度な権限を必要はありません。 たとえば、一般に、データベースにアクセスする SQL ログインを使用して、組織内のユーザーには、昇格されたアクセス許可がありません。 そのため、R または Python を使用しているユーザーごとにする必要がありますユーザーに付与する Machine Learning サービスの言語が使用されている各データベースで外部のスクリプトを実行するアクセス許可。 次の手順に従います。

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> 権限はサポートされているスクリプト言語に固有ではありません。 つまり、R スクリプトのスクリプトと Python スクリプトの個別のアクセス許可レベルがありません。 これらの言語の個別のアクセス許可を維持する必要がある場合は、個別のインスタンスに R と Python をインストールします。

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>データベースのアクセス許可の付与

ユーザーがスクリプトを実行中に、ユーザーが他のデータベースからデータを読み取る必要があります。 ユーザーは、結果の保存、およびテーブルにデータを記述する新しいテーブルを作成する必要もあります。

Windows ユーザー アカウントまたは R または Python スクリプトを実行している SQL ログインごとに、特定のデータベースに対する適切なアクセス許可があることを確認します:`db_datareader`データを読み取る`db_datawriter`オブジェクトをデータベースに保存するか、`db_ddladmin`オブジェクトを作成するにはストアド プロシージャやテーブルなどを含むはトレーニングし、データをシリアル化します。

たとえば、次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、SQL ログイン*MySQLLogin*で T-SQL クエリを実行する権限、 *ML_Samples*データベース。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>次の手順

各ロールに含まれるアクセス許可の詳細については、次を参照してください。[データベース レベル ロール](../../relational-databases/security/authentication-access/database-level-roles.md)します。