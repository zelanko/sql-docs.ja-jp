---
title: SQL Server Machine Learning サービスへのアクセス許可をユーザーに付与 |Microsoft Docs
description: SQL Server Machine Learning サービスへのアクセス許可をユーザーに付与する方法。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: ad5c3fa3bf94bb88041c9ec81773b2a26013e517
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100333"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>SQL Server Machine Learning サービスへのアクセス許可をユーザーに付与します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、どのユーザーに付与できます SQL Server Machine Learning サービスで外部のスクリプトを実行して、読み取り、書き込み、またはデータの定義のデータベースへの言語 (DDL) のアクセス許可を付与するアクセス許可について説明します。

SQL Server のデータを使用するか、計算コンテキストとして SQL Server を実行する外部のスクリプトを実行するには、SQL Server ログインまたは Windows ユーザー アカウントが必要です。

ログインまたはユーザー アカウントを識別、*セキュリティ プリンシパル*、複数レベルの外部スクリプトの要件に応じて、アクセスする必要があります。

+ 外部スクリプトが有効になっているデータベースにアクセスする権限です。
+ テーブルなどのセキュリティで保護されたオブジェクトからデータを読み取るアクセス許可。
+ モデルをスコア付けの結果など、テーブルに新しいデータを書き込む権限です。
+ テーブルなどの新しいオブジェクトを作成する機能には、外部のスクリプトを使用するプロシージャが格納されているか、カスタム関数を使用して R または Python ジョブ。
+ SQL Server コンピューターでは、新しいパッケージをインストールまたはユーザーのグループに提供されるパッケージを使用する権限。

そのため、実行コンテキストとして SQL Server を使用して外部スクリプトを実行する各ユーザーは、データベース内のユーザーにマップする必要があります。 SQL Server のセキュリティのアクセス許可のセットを管理し、これらのロールにユーザーの割り当てではなくユーザーのアクセス許可を個別に設定するロールを作成する最も簡単ななります。

外部ツールで R または Python を使用しているユーザーもは、ユーザーは、外部スクリプト (データベース内)、または access データベース オブジェクトとデータを実行する必要がある場合、ログインまたはデータベース内のアカウントにマップする必要があります。 外部スクリプトのリモート データ サイエンス クライアントから送信されるまたは T-SQL ストアド プロシージャの使用を開始するかどうか、同じアクセス許可が必要です。

たとえば、ローカル コンピューターで実行されている外部スクリプトを作成して、SQL Server でそのコードを実行します。 次の条件が満たされていることを確認する必要があります。

+ データベースがリモート接続を許可します。
+ インスタンス レベルでの SQL Server、SQL ログインまたはデータベースへのアクセスに使用した Windows アカウントが追加されました。
+ SQL ログインまたは Windows ユーザーには、外部スクリプトを実行するアクセス許可がある場合があります。 一般に、このアクセス許可を追加できるのはデータベース管理者のみです。
+ SQL ログインまたは Window ユーザーは、各データベースの外部のスクリプトを実行してこれらの操作のいずれかで、適切なアクセス許可を持つユーザーとして追加する必要があります。
  + データを取得しています。
  + 書き込みやデータを更新します。
  + テーブルやストアド プロシージャなどの新しいオブジェクトを作成します。

ログインまたは Windows ユーザー アカウントをプロビジョニングし、必要なアクセス許可を付与されていますが、後に SQL Server での外部のスクリプトを実行 R でデータ ソース オブジェクトを使用して、または**revoscalepy**ライブラリでは、Python、または保存を呼び出すことによって外部スクリプトを含むプロシージャです。

SQL Server から外部のスクリプトを起動するたびに、データベース エンジン セキュリティは、ジョブを開始し、ユーザーまたはセキュリティ保護可能なオブジェクトへのログインのマッピングを管理ユーザーのセキュリティ コンテキストを取得します。

そのため、リモート クライアントから開始されるすべての外部スクリプトでは、接続文字列の一部としてログインまたはユーザー情報を指定する必要があります。

<a name="permissions-external-script"></a> 

## <a name="permission-to-run-scripts"></a>スクリプトを実行するためのアクセス許可

インストールした場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]して、自分で独自のインスタンスで R または Python スクリプトの実行は、通常、管理者としてスクリプトを実行します。 したがって、さまざまな操作と、データベース内のすべてのデータに対する暗黙的なアクセス許可があります。

ただし、ほとんどのユーザーは、このような高度な権限を必要はありません。 たとえば、一般に、データベースにアクセスする SQL ログインを使用して、組織内のユーザーには、昇格されたアクセス許可がありません。 そのため、R または Python を使用しているユーザーごとにする必要がありますユーザーに付与する Machine Learning サービスの言語が使用されている各データベースで外部のスクリプトを実行するアクセス許可。 ここではどのように。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> 権限はサポートされているスクリプト言語に固有ではありません。 つまり、R スクリプトのスクリプトと Python スクリプトの個別のアクセス許可レベルがありません。 これらの言語の個別のアクセス許可を維持する必要がある場合は、個別のインスタンスに R と Python をインストールします。

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>データベースのアクセス許可の付与

ユーザーがスクリプトを実行中に、ユーザーが他のデータベースからデータを読み取る必要があります。 ユーザーは、結果の保存、およびテーブルにデータを記述する新しいテーブルを作成する必要もあります。

Windows ユーザー アカウントまたは R または Python スクリプトを実行している SQL ログインごとに、特定のデータベースに対する適切なアクセス許可があることを確認します:`db_datareader`データを読み取る`db_datawriter`オブジェクトをデータベースに保存するか、`db_ddladmin`オブジェクトを作成するにはストアド プロシージャやテーブルなどを含むはトレーニングし、データをシリアル化します。

たとえば、次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、SQL ログイン*MySQLLogin*で T-SQL クエリを実行する権限、 *ML_Samples*データベース。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>次の手順

各ロールに含まれるアクセス許可の詳細については、次を参照してください。[データベース レベル ロール](../../relational-databases/security/authentication-access/database-level-roles.md)します。