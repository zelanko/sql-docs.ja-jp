---
title: "セキュリティの概要 (SQL Server R サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6ddfc3ccb67d017dc618cfbb7e7680c0164f3a21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="security-overview"></a>セキュリティの概要

このトピックの接続に使用されるセキュリティ アーキテクチャについて説明、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データベース エンジンおよび Python コンポーネントです。 2 つの一般的なシナリオについて、セキュリティ処理の例が記載されて: ストアド プロシージャを使用して、リモート計算コンテキストとして SQL Server で Python を実行している SQL Server で Python を実行します。

## <a name="security-overview"></a>セキュリティの概要

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL Server での Python スクリプトを実行するログインまたは Windows ユーザー アカウントが必要です。 ログインまたはユーザー アカウントを識別、*セキュリティ プリンシパル*、データベースからデータを取得する場所にアクセスする権限を持つ必要があります。 Python スクリプトが新しいオブジェクトを作成か、新しいデータを書き込むか、によって、ユーザーは、テーブルを作成、データを書き込む、またはカスタム関数またはストアド プロシージャを作成するアクセス許可を必要があります。

そのため、厳密な要件がする Python コードを実行する各ユーザーに[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ログインまたはデータベース内のアカウントにマップする必要があります。 この制限は、スクリプトは、リモート データ サイエンス クライアントから送信するかどうかに関係なく適用されます。 または T-SQL ストアド プロシージャの使用を開始します。

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


## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] セキュリティとスタート パッド セキュリティの相互作用

コンテキストでの Python スクリプトを実行すると、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 、コンピューター、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]サービスの外部プロセス用に確立されたワーカー アカウントのプールから使用可能なワーカー アカウント (ローカル ユーザー アカウント) を取得およびはそのワーカー アカウントを使用関連するタスクを実行します。

たとえば、Windows ドメインの資格情報 Python スクリプトを起動するとします。 SQL Server は、資格情報を取得し、など、使用可能なスタート パッドのワーカー アカウントにマップする*SQLRUser01*です。

> [!NOTE]
> ワーカー アカウントのグループの名前は、R または Python のどちらを使用しているかどうかに関係なく同じです。 ただし、別のグループは、外部の言語を有効にするインスタンスごとに作成されます。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] は、ワーカー アカウントへのマッピングの後で、プロセスの開始に使用されるユーザー トークンを作成します。 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のすべての処理が完了すると、ユーザー ワーカー アカウントは空きとしてマークされ、プールに返されます。

詳細については[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]を参照してください[Python の統合をサポートする SQL Server の新しいコンポーネント](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md)です。

> [!NOTE]
> ワーカー アカウントを管理し、Python ジョブ、ワーカー アカウントが含まれるグループを実行するスタート パッドの*SQLRUserGroup*、権限が必要「ログオンを許可するローカル」です。 それ以外の場合、Python、ランタイムが開始されていません。 既定では、この権限はすべての新しいローカル ユーザーに与えられますが一部の組織でグループ ポリシーをより厳密な可能性があります強制する、Python ジョブに SQL Server への接続からワーカー アカウントを回避します。

## <a name="security-of-worker-accounts"></a>ワーカー アカウントのセキュリティ

外部の Windows ユーザーまたはワーカー アカウントに有効な SQL ログインのマッピングは、Python スクリプトを実行する SQL の有効期間はストアド プロシージャに対してのみ有効です。

同じログインからの並列クエリは、同じユーザー ワーカー アカウントにマップされます。

管理されるプロセス用に使用されるディレクトリ、 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]、およびディレクトリはアクセスを制限します。 Python の PythonLauncher はこのタスクを実行します。 それぞれ個別のワーカー アカウントは、独自のフォルダーには制限され、独自レベルより上のフォルダー内のファイルにアクセスできません。 ただし、ワーカー アカウントを読み取り、書き込み、または作成されたセッションの作業フォルダーの下の子を削除します。

ワーカー アカウントの数、アカウント名、またはアカウント パスワードを変更する方法について詳しくは、「[Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)」(SQL Server R Services のユーザー アカウント プールの変更) を参照してください。


## <a name="security-isolation-for-multiple-external-scripts"></a>複数外部スクリプトでのセキュリティ分離

分離メカニズムは物理ユーザー アカウントに基づいています。 サテライト プロセスは特定の言語ラインタイムに対して開始されるため、各サテライト タスクは [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] によって指定されたワーカー アカウントを使用します。 タスクが複数のサテライトを必要とする場合 (たとえば並列クエリなど)、関連するすべてのタスクで 1 つのワーカー アカウントが使用されます。

ワーカー アカウントは、他のワーカー アカウントによって使用されるファイルを、読み取ったり操作したりすることはできません。

コンピューターの管理者であれば、各プロセスによって作成されたディレクトリを表示できます。 各ディレクトリはセッション GUID によって識別されます。

## <a name="see-also"></a>参照

[アーキテクチャの概要](../../advanced-analytics/python/architecture-overview-sql-server-python.md)

