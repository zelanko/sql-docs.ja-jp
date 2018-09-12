---
title: SQL Server Machine Learning での Python のセキュリティの概要 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a33701283635327fcaac4a9629cb02044b30dda8
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890058"
---
# <a name="security-overview-for-python-in-sql-server-machine-learning"></a>SQL Server Machine Learning での Python のセキュリティの概要
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このトピックでは、接続に使用されるセキュリティ アーキテクチャを説明します、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データベース エンジンおよび Python コンポーネント。 2 つの一般的なシナリオ、セキュリティ プロセスの例を示します。 ストアド プロシージャを使用すると、リモート計算コンテキストとして SQL Server での Python を実行している SQL Server で Python を実行します。

## <a name="security-overview"></a>セキュリティの概要

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL Server での Python スクリプトを実行するログインまたは Windows ユーザー アカウントが必要です。 これら*セキュリティ プリンシパル*インスタンスとデータベース レベルで管理されますと、データベースへの接続、読み取りと、データを書き込みアクセス許可を持つユーザーを識別またはテーブルやストアド プロシージャなどのデータベース オブジェクトを作成します。 さらに、Python スクリプトを実行しているユーザーには、データベース レベルでの外部のスクリプトを実行する権限が必要です。

外部ツールで Python を使用しているユーザーもは、ユーザーは、Python コードでのデータベース、または access データベース オブジェクトおよびデータを実行する必要がある場合、ログインまたはデータベース内のアカウントにマップする必要があります。 Python スクリプトをリモート データ サイエンス クライアントから送信されるまたは T-SQL ストアド プロシージャの使用を開始するかどうか、同じアクセス許可が必要です。

たとえば、ラップトップ コンピューターで実行される Python スクリプトを作成することでそのコードを実行する[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。 次の条件が満たされていることを確認する必要があります。

+ データベースがリモート接続を許可します。
+ SQL ログインまたはデータベースへのアクセスに使用した Windows アカウントに追加された、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンス レベルでします。
+ SQL ログインまたは Windows ユーザーには、外部スクリプトを実行するアクセス許可を付与する必要があります。 一般に、このアクセス許可を追加できるのはデータベース管理者のみです。
+ SQL ログインまたは Window ユーザーは、Python スクリプトを実行してこれらの操作のいずれかの各データベース内の適切なアクセス許可を持つユーザーとして追加する必要があります。
    + データの取得
    + データの作成または更新
    + 新しいオブジェクト (テーブルやストアド プロシージャなど) の作成

ログインまたは Windows ユーザー アカウントをプロビジョニングし、必要なアクセス許可を付与されていますが後で Python コードを実行できます[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]によって提供されるデータ ソース オブジェクトを使用して、 **revoscalepy**ライブラリ、または保存を呼び出すことによってPython スクリプトを含むプロシージャです。

Python スクリプトを起動するたびに[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、データベース エンジンのセキュリティは、ジョブを開始し、ユーザーまたはセキュリティ保護可能なオブジェクトへのログインのマッピングを管理ユーザーのセキュリティ コンテキストを取得します。

そのため、リモート クライアントから開始されるすべての Python スクリプトでは、接続文字列の一部としてログインまたはユーザー情報を指定する必要があります。

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>相互作用[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]セキュリティとスタート パッド セキュリティ

コンテキストでの Python スクリプトを実行すると、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 、コンピューター、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]サービスの外部プロセス用に確立されたワーカー アカウントのプールから使用可能なワーカー アカウント (ローカル ユーザー アカウント) を取得し、ワーカー アカウントを使用します。関連するタスクを実行します。

たとえば、Windows ドメインの資格情報で Python スクリプトを起動するとします。 SQL Server は、資格情報を取得およびなど、タスクを使用可能なスタート パッド ワーカー アカウントにマップ*SQLRUser01*します。

> [!NOTE]
> ワーカー アカウントのグループの名前は、R または Python を使用しているかどうかに関係なく同じです。 ただし、別のグループは、任意の外部の言語を有効にするインスタンスごとに作成されます。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] は、ワーカー アカウントへのマッピングの後で、プロセスの開始に使用されるユーザー トークンを作成します。 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のすべての処理が完了すると、ユーザー ワーカー アカウントは空きとしてマークされ、プールに返されます。

サービスの詳細については、次を参照してください。 [Extensibility framework](../concepts/extensibility-framework.md)します。

### <a name="implied-authentication"></a>暗黙の認証

**暗黙の認証**は SQL Server がユーザーを取得するプロセスで使用される用語の資格情報し、データベースに適切なアクセス許可をユーザーがあると仮定すると、ユーザーに代わってすべての外部のスクリプト タスクを実行します。 暗黙の認証は、Python スクリプトは、SQL Server データベースの外部の ODBC 呼び出しを行う必要がある場合に特に重要です。 たとえば、コードでは、スプレッドシートまたはその他のソースから要因の短いリストを取得する可能性があります。

このようなループバック呼び出しが成功するには、グループ SQLRUserGroup が、ワーカー アカウントを含む「ローカル ログオンを許可」権限が必要です。 既定では、すべての新しいローカル ユーザーにこの権限が与えられますが、一部の組織では、厳しいグループ ポリシーを適用する場合があります。

![R の暗黙の認証](media/implied-auth-python2.png)

## <a name="security-of-worker-accounts"></a>ワーカー アカウントのセキュリティ

外部の Windows ユーザーまたはワーカー アカウントの有効な SQL ログインのマッピングでは、Python スクリプトを実行する SQL の有効期間はストアド プロシージャに対してのみ有効です。

同じログインからの並列クエリは、同じユーザー ワーカー アカウントにマップされます。

プロセスで使用されるディレクトリで管理されて、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]ディレクトリは、アクセスが制限されたとします。 Python の場合は、PythonLauncher は、このタスクを実行します。 個々 のワーカー アカウントごとでは、独自のフォルダーには制限され、独自のレベル上にあるフォルダー内のファイルにアクセスできません。 ただし、ワーカー アカウントは読み取り、書き込み、または作成されたセッション作業フォルダーの下の子を削除します。

ワーカー アカウント、アカウント名、またはアカウントのパスワードの数を変更する方法の詳細については、次を参照してください。 [SQL Server machine learning のユーザー アカウント プールを変更する](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)します。


## <a name="security-isolation-for-multiple-external-scripts"></a>複数の外部スクリプトのセキュリティの分離

分離メカニズムは物理ユーザー アカウントに基づいています。 サテライト プロセスは特定の言語ラインタイムに対して開始されるため、各サテライト タスクは [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] によって指定されたワーカー アカウントを使用します。 タスクが複数のサテライトを必要とする場合 (たとえば並列クエリなど)、関連するすべてのタスクで 1 つのワーカー アカウントが使用されます。

ワーカー アカウントは、他のワーカー アカウントによって使用されるファイルを、読み取ったり操作したりすることはできません。

コンピューターの管理者であれば、各プロセスによって作成されたディレクトリを表示できます。 各ディレクトリはセッション GUID によって識別されます。

## <a name="see-also"></a>参照

[アーキテクチャの概要](../../advanced-analytics/python/architecture-overview-sql-server-python.md)
