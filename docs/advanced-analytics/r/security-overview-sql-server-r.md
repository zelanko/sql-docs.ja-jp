---
title: SQL Server machine learning と R のセキュリティ |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c04670464d23f0951a957df945a2e81b817ae134
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889188"
---
# <a name="security-for-sql-server-machine-learning-and-r"></a>SQL Server machine learning と R のセキュリティ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、接続に使用される全体的なセキュリティ アーキテクチャをについて説明します、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データベース エンジンと R ランタイムに関連するコンポーネント。 セキュリティ プロセスの例では、エンタープライズ環境で R を使用するためのこれらの一般的なシナリオを示します。

+ データ サイエンス クライアントから [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で RevoScaleR 関数 を実行
+ ストアド プロシージャを使用して R を [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] から直接実行

## <a name="security-overview"></a>セキュリティの概要

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL Server のデータを使用するか、計算コンテキストとして SQL Server を実行する R スクリプトを実行するログインまたは Windows ユーザー アカウントが必要です。 この要件は、両方に適用されます[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]および SQL Server 2017[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]します。

ログインまたはユーザー アカウントを識別、*セキュリティ プリンシパル*、複数レベルの R スクリプトの要件に応じて、アクセスする必要があります。

+ R が有効になっているデータベースにアクセスします。
+ テーブルなどのセキュリティで保護されたオブジェクトからデータを読み取るアクセス許可
+ モデルをスコア付けの結果など、テーブルに新しいデータを記述する機能
+ テーブルなどの新しいオブジェクトを作成する機能には、R スクリプトを使用するプロシージャが格納されているか、カスタム関数を使用して R ジョブ
+ SQL Server のコンピューターまたはユーザーのグループに提供される R を使用してパッケージに新しいパッケージをインストールする権限。 

使用して R コードを実行する各ユーザーつまり[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]として、実行コンテキストは、データベースのログインにマップする必要があります。 SQL Server のセキュリティでは、一般に、アクセス許可のセットを管理し、これらのロールにユーザーの割り当てではなくユーザーのアクセス許可を個別に設定するロールを作成する最も簡単ななります。 

例として、ラップトップ コンピューターで実行されているいくつかの R コードを作成してでそのコードを実行することを想定[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。 これは、これらの条件が満たされた場合にのみ行うことができます。

+ データベースがリモート接続を許可します。
+ R コードで使用した名前とパスワードの SQL ログインが、インスタンス レベルで [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] に追加されています。 または、Windows 統合認証を使用している場合は、接続文字列に指定された Windows ユーザーがインスタンスにユーザーとして追加されている必要があります。
+ SQL ログインまたは Windows ユーザーには、外部スクリプトを実行するアクセス許可がある場合があります。 一般に、このアクセス許可を追加できるのはデータベース管理者のみです。
+ SQL ログインまたは Window ユーザーは、R ジョブが次の処理を実行する各データベースに、適切なアクセス許可を持つユーザーとして追加される必要があります。
    + データの取得
    + データの作成または更新 
    + 新しいオブジェクト (テーブルやストアド プロシージャなど) の作成

ログインまたは Windows ユーザー アカウントをプロビジョニングし、必要なアクセス許可を付与されていますが後、R コードを実行できます[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]R データ ソース オブジェクトを使用して、またはストアド プロシージャを呼び出すことによって。 R を起動するたびに[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、データベース エンジンのセキュリティは、R ジョブを開始またはストアド プロシージャを実行し、ユーザーまたはセキュリティ保護可能なオブジェクトへのログインのマッピングを管理ユーザーのセキュリティ コンテキストを取得します。 

そのため、リモート クライアントから開始されるすべての R ジョブでは、接続文字列の一部としてログインまたはユーザー情報を指定する必要があります。

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>相互作用[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]セキュリティとスタート パッド セキュリティ

R スクリプトが [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターのコンテキストで実行されるとき、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスは、外部プロセス用に確立されたワーカー アカウントのプールから使用可能なワーカー アカウント (ローカル ユーザー アカウント) を取得し、そのワーカー アカウントを使用して関連するタスクを実行します。 

たとえば、自分の Windows ドメイン資格情報で R ジョブを開始すると、そのアカウントがスタート パッドのワーカー アカウント *SQLRUser01* にマップされることがあります。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] は、ワーカー アカウントへのマッピングの後で、プロセスの開始に使用されるユーザー トークンを作成します。 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のすべての処理が完了すると、ユーザー ワーカー アカウントは空きとしてマークされ、プールに返されます。

サービスの詳細については、次を参照してください。 [Extensibility framework](../concepts/extensibility-framework.md)します。 

### <a name="implied-authentication"></a>暗黙の認証

**暗黙の認証**は SQL Server がユーザーを取得するプロセスで使用される用語の資格情報し、データベースに適切なアクセス許可をユーザーがあると仮定すると、ユーザーに代わってすべての外部のスクリプト タスクを実行します。 暗黙の認証は、R スクリプトは、SQL Server データベースの外部の ODBC 呼び出しを行う必要がある場合に特に重要です。 たとえば、コードでは、スプレッドシートまたはその他のソースから要因の短いリストを取得する可能性があります。

このようなループバック呼び出しが成功するには、グループ SQLRUserGroup が、ワーカー アカウントを含む「ローカル ログオンを許可」権限が必要です。 既定では、すべての新しいローカル ユーザーにこの権限が与えられますが、一部の組織では、厳しいグループ ポリシーを適用する場合があります。

![R の暗黙の認証](media/implied-auth-rsql.png)

## <a name="security-of-worker-accounts"></a>ワーカー アカウントのセキュリティ

外部の Windows ユーザーまたはワーカー アカウントの有効な SQL ログインのマッピングは、R スクリプトを実行する SQL クエリの有効期間の有効期間でのみ有効です。

同じログインからの並列クエリは、同じユーザー ワーカー アカウントにマップされます。

プロセスで使用されるディレクトリは、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] が RLauncher を使用して管理します。ディレクトリへのアクセスは制限されます。 ワーカー アカウントは、自分のフォルダーよりも上にあるフォルダー内のファイルにはアクセスできません。ただし、R スクリプトを含む SQL クエリのために作成されたセッション作業フォルダー内の子ファイルの読み取り、書き込み、削除は行うことができます。

ワーカー アカウント、アカウント名、またはアカウントのパスワードの数を変更する方法の詳細については、次を参照してください。 [SQL Server machine learning のユーザー アカウント プールを変更する](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)します。

## <a name="security-isolation-for-multiple-external-scripts"></a>複数の外部スクリプトのセキュリティの分離

分離メカニズムは物理ユーザー アカウントに基づいています。 サテライト プロセスは特定の言語ラインタイムに対して開始されるため、各サテライト タスクは [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] によって指定されたワーカー アカウントを使用します。 タスクが複数のサテライトを必要とする場合 (たとえば並列クエリなど)、関連するすべてのタスクで 1 つのワーカー アカウントが使用されます。

ワーカー アカウントは、他のワーカー アカウントによって使用されるファイルを、読み取ったり操作したりすることはできません。
 
コンピューターの管理者であれば、各プロセスによって作成されたディレクトリを表示できます。 各ディレクトリはセッション GUID によって識別されます。

## <a name="see-also"></a>関連項目

[SQL Server machine learning のアーキテクチャの概要](../../advanced-analytics/r/architecture-overview-sql-server-r.md)
