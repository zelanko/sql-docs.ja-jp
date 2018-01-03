---
title: "SQL Server での Python のセキュリティの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 7cddb2d641db20ae18a6c6cbbe63afd341a18a2e
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="security-overview-for-python-in-sql-server"></a>SQL Server での Python のセキュリティの概要

このトピックの接続に使用されるセキュリティ アーキテクチャについて説明、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データベース エンジンおよび Python コンポーネントです。 2 つの一般的なシナリオについて、セキュリティ処理の例が記載されて: ストアド プロシージャを使用して、リモート計算コンテキストとして SQL Server で Python を実行している SQL Server で Python を実行します。

## <a name="security-overview"></a>セキュリティの概要

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL Server での Python スクリプトを実行するログインまたは Windows ユーザー アカウントが必要です。 これら*セキュリティ プリンシパル*インスタンスおよびデータベース レベルでは、管理し、データベースへの接続、読み書き可能なデータへのアクセス許可を持つユーザーを識別またはテーブルやストアド プロシージャなどのデータベース オブジェクトを作成します。 また、Python スクリプトを実行しているユーザーには、データベース レベルでの外部のスクリプトを実行する権限が必要です。

外部ツールで Python を使用しているユーザーであってもは、ユーザーは、Python コード内のデータベース、またはデータベース オブジェクトとデータを実行する必要がある場合、ログインまたはデータベース内のアカウントにマップする必要があります。 Python スクリプトのリモート データ サイエンス クライアントから送信されるまたは T-SQL ストアド プロシージャを使用して開始されたかどうか、同じアクセス許可が必要です。

たとえば、ラップトップ コンピューターで実行されている Python スクリプトを作成してでそのコードを実行すること[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 次の条件が満たされていることを確認する必要があります。

+ データベースがリモート接続を許可します。
+ SQL ログインまたはデータベースへのアクセスに使用した Windows アカウントに追加された、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンス レベルでします。
+ SQL ログインまたは Windows ユーザーには、外部スクリプトを実行するアクセス許可を付与する必要があります。 一般に、このアクセス許可を追加できるのはデータベース管理者のみです。
+ SQL ログインまたはウィンドウのユーザーは、Python スクリプトを実行してこれらの操作のいずれかの各データベースでの適切な権限を持つユーザーとして追加する必要があります。
    + データの取得
    + データの作成または更新
    + 新しいオブジェクト (テーブルやストアド プロシージャなど) の作成

Python コードを実行するにはログインまたは Windows ユーザー アカウントをプロビジョニングされ、必要なアクセス許可が付与されているが、されたら[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]によって提供されるデータ ソース オブジェクトを使用して、 **revoscalepy**ライブラリ、または保存を呼び出すことによってPython スクリプトを含むプロシージャです。

Python スクリプトを起動するたびに[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、データベース エンジンのセキュリティは、ジョブを開始し、ユーザーまたはセキュリティ保護可能なオブジェクトへのログインのマッピングを管理するユーザーのセキュリティ コンテキストを取得します。

したがって、リモート クライアントから開始されるすべての Python スクリプトでは、接続文字列の一部としてログインまたはユーザーの情報を指定する必要があります。

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>相互作用[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]セキュリティとスタート パッドのセキュリティ

コンテキストでの Python スクリプトを実行すると、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 、コンピューター、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]サービスの外部プロセス用に確立されたワーカー アカウントのプールから使用可能なワーカー アカウント (ローカル ユーザー アカウント) を取得およびはそのワーカー アカウントを使用関連するタスクを実行します。

たとえば、Windows ドメインの資格情報 Python スクリプトを起動するとします。 SQL Server は、資格情報を取得およびなど、使用可能なスタート パッド ワーカー アカウントをタスクをマップ*SQLRUser01*です。

> [!NOTE]
> ワーカー アカウントのグループの名前は、R または Python のどちらを使用しているかどうかに関係なく同じです。 ただし、別のグループは、外部の言語を有効にするインスタンスごとに作成されます。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] は、ワーカー アカウントへのマッピングの後で、プロセスの開始に使用されるユーザー トークンを作成します。 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のすべての処理が完了すると、ユーザー ワーカー アカウントは空きとしてマークされ、プールに返されます。

詳細については[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]を参照してください[Python 統合をサポートするために SQL Server のコンポーネント](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md)です。

### <a name="implied-authentication"></a>暗黙の認証

**黙示的な認証**は、SQL Server がユーザーを取得する処理に使用される用語の資格情報し、ユーザーがデータベースに適切なアクセス許可を持つと仮定した場合、ユーザーの代理のすべての外部のスクリプト タスクを実行します。 黙示的な認証は、Python スクリプトは、SQL Server データベースの外部の ODBC 呼び出しを行う必要がある場合に特に重要です。 たとえば、コードでは、スプレッドシートまたはその他のソースから要因の短い一覧を取得する可能性があります。

このようなループバック呼び出しが成功するには、ワーカー アカウント、SQLRUserGroup を含むグループは「ローカル ログオンを許可」権限が必要です。 既定では、この権限はすべての新しいローカル ユーザーに与えられますが、一部の組織より厳密なグループ ポリシーを適用する場合があります。

![R の暗黙の認証](media/implied-auth-python2.png)

## <a name="security-of-worker-accounts"></a>ワーカー アカウントのセキュリティ

外部の Windows ユーザーまたはワーカー アカウントに有効な SQL ログインのマッピングは、Python スクリプトを実行する SQL の有効期間はストアド プロシージャに対してのみ有効です。

同じログインからの並列クエリは、同じユーザー ワーカー アカウントにマップされます。

管理されるプロセス用に使用されるディレクトリ、 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]、およびディレクトリはアクセスを制限します。 Python の PythonLauncher はこのタスクを実行します。 それぞれ個別のワーカー アカウントは、独自のフォルダーには制限され、独自レベルより上のフォルダー内のファイルにアクセスできません。 ただし、ワーカー アカウントを読み取り、書き込み、または作成されたセッションの作業フォルダーの下の子を削除します。

ワーカー アカウント、アカウント名、またはアカウントのパスワードの数を変更する方法の詳細については、次を参照してください。[機械学習の SQL Server のユーザー アカウント プールを変更する](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)です。


## <a name="security-isolation-for-multiple-external-scripts"></a>複数の外部スクリプトのセキュリティの分離

分離メカニズムは、物理的なユーザー アカウントに基づいています。 サテライト プロセスは特定の言語ラインタイムに対して開始されるため、各サテライト タスクは [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] によって指定されたワーカー アカウントを使用します。 タスクが複数のサテライトを必要とする場合 (たとえば並列クエリなど)、関連するすべてのタスクで 1 つのワーカー アカウントが使用されます。

ワーカー アカウントは、他のワーカー アカウントによって使用されるファイルを、読み取ったり操作したりすることはできません。

コンピューターの管理者であれば、各プロセスによって作成されたディレクトリを表示できます。 各ディレクトリはセッション GUID によって識別されます。

## <a name="see-also"></a>参照

[アーキテクチャの概要](../../advanced-analytics/python/architecture-overview-sql-server-python.md)
