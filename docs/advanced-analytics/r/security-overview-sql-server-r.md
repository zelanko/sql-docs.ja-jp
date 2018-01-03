---
title: "SQL Server の機械学習と R のセキュリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dba0ea904e9b22cb99e4e0deb9befc32dd9e1abe
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="security-for-sql-server-machine-learning-and-r"></a>SQL Server の機械学習と R のセキュリティ

この記事は、接続に使用される全体的なセキュリティ アーキテクチャをについて説明します、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データベース エンジンと R ランタイムに関連するコンポーネントです。 R を使用するエンタープライズ環境でこれらの一般的なシナリオについては、セキュリティ処理の例が用意されています。

+ データ サイエンス クライアントから [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で RevoScaleR 関数 を実行
+ ストアド プロシージャを使用して R を [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] から直接実行

## <a name="security-overview"></a>セキュリティの概要

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL Server のデータを使用するか、計算コンテキストとして SQL Server を実行する R スクリプトを実行するログインまたは Windows ユーザー アカウントが必要です。 この要件は、両方に適用されます。[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]と SQL Server 2017[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]です。

ログインまたはユーザー アカウントを識別、*セキュリティ プリンシパル*、複数レベルのアクセス、R スクリプトの要件に応じて必要がある可能性があります。

+ R が有効になっているデータベースにアクセスする権限
+ テーブルなどのセキュリティで保護されたオブジェクトからデータを読み取るアクセス許可
+ モデル、または結果をスコア付けなど、テーブルに新しいデータを書き込む機能
+ テーブルなどの新しいオブジェクトを作成するストアド プロシージャを R スクリプトを使用するか、カスタム関数を使用する R ジョブ
+ SQL Server コンピューターまたはユーザーのグループに提供された R を使用してパッケージに新しいパッケージをインストールする権限。 

使用して R コードを実行する各ユーザーそのため、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]実行した場合とは、コンテキストをデータベース内のログインにマップする必要があります。 SQL Server のセキュリティは、一般に、アクセス許可のセットを管理し、これらのロールにユーザーの割り当てではなくユーザーのアクセス許可を個別に設定するロールを作成する最も簡単なです。 

例としてでそのコードを実行して、ラップトップで実行されているいくつかの R コードを作成したであると[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 これは、これらの条件が満たされた場合にのみ行うことができます。

+ データベースがリモート接続を許可します。
+ R コードで使用した名前とパスワードの SQL ログインが、インスタンス レベルで [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] に追加されています。 または、Windows 統合認証を使用している場合は、接続文字列に指定された Windows ユーザーがインスタンスにユーザーとして追加されている必要があります。
+ SQL ログインまたは Windows ユーザーには、外部のスクリプトを実行するアクセス許可がある場合があります。 一般に、このアクセス許可を追加できるのはデータベース管理者のみです。
+ SQL ログインまたは Window ユーザーは、R ジョブが次の処理を実行する各データベースに、適切なアクセス許可を持つユーザーとして追加される必要があります。
    + データの取得
    + データの作成または更新 
    + 新しいオブジェクト (テーブルやストアド プロシージャなど) の作成

R コードを実行するにはログインまたは Windows ユーザー アカウントをプロビジョニングされ、必要なアクセス許可が付与されているが、されたら[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]R データ ソース オブジェクトを使用して、またはストアド プロシージャを呼び出すことによってです。 R が開始されるたびに[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、データベース エンジンのセキュリティは、R ジョブを開始またはストアド プロシージャを実行し、ユーザーまたはセキュリティ保護可能なオブジェクトへのログインのマッピングを管理するユーザーのセキュリティ コンテキストを取得します。 

そのため、リモート クライアントから開始されるすべての R ジョブでは、接続文字列の一部としてログインまたはユーザー情報を指定する必要があります。

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>相互作用[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]セキュリティとスタート パッドのセキュリティ

R スクリプトが [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターのコンテキストで実行されるとき、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスは、外部プロセス用に確立されたワーカー アカウントのプールから使用可能なワーカー アカウント (ローカル ユーザー アカウント) を取得し、そのワーカー アカウントを使用して関連するタスクを実行します。 

たとえば、自分の Windows ドメイン資格情報で R ジョブを開始すると、そのアカウントがスタート パッドのワーカー アカウント *SQLRUser01* にマップされることがあります。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] は、ワーカー アカウントへのマッピングの後で、プロセスの開始に使用されるユーザー トークンを作成します。 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のすべての処理が完了すると、ユーザー ワーカー アカウントは空きとしてマークされ、プールに返されます。

詳細については[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]を参照してください[R 統合をサポートするために SQL Server のコンポーネント](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)です。

### <a name="implied-authentication"></a>暗黙の認証

**黙示的な認証**は、SQL Server がユーザーを取得する処理に使用される用語の資格情報し、ユーザーがデータベースに適切なアクセス許可を持つと仮定した場合、ユーザーの代理のすべての外部のスクリプト タスクを実行します。 黙示的な認証は、R スクリプトは、SQL Server データベースの外部の ODBC 呼び出しを行う必要がある場合に特に重要です。 たとえば、コードでは、スプレッドシートまたはその他のソースから要因の短い一覧を取得する可能性があります。

このようなループバック呼び出しが成功するには、ワーカー アカウント、SQLRUserGroup を含むグループは「ローカル ログオンを許可」権限が必要です。 既定では、この権限はすべての新しいローカル ユーザーに与えられますが、一部の組織より厳密なグループ ポリシーを適用する場合があります。

![R の暗黙の認証](media/implied-auth-rsql.png)

## <a name="security-of-worker-accounts"></a>ワーカー アカウントのセキュリティ

外部の Windows ユーザーまたはワーカー アカウントに有効な SQL ログインのマッピングは、R スクリプトを実行する SQL クエリの有効期間の有効期間にのみ有効です。

同じログインからの並列クエリは、同じユーザー ワーカー アカウントにマップされます。

プロセスで使用されるディレクトリは、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] が RLauncher を使用して管理します。ディレクトリへのアクセスは制限されます。 ワーカー アカウントは、自分のフォルダーよりも上にあるフォルダー内のファイルにはアクセスできません。ただし、R スクリプトを含む SQL クエリのために作成されたセッション作業フォルダー内の子ファイルの読み取り、書き込み、削除は行うことができます。

ワーカー アカウント、アカウント名、またはアカウントのパスワードの数を変更する方法の詳細については、次を参照してください。[機械学習の SQL Server のユーザー アカウント プールを変更する](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

## <a name="security-isolation-for-multiple-external-scripts"></a>複数の外部スクリプトのセキュリティの分離

分離メカニズムは物理ユーザー アカウントに基づいています。 サテライト プロセスは特定の言語ラインタイムに対して開始されるため、各サテライト タスクは [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] によって指定されたワーカー アカウントを使用します。 タスクが複数のサテライトを必要とする場合 (たとえば並列クエリなど)、関連するすべてのタスクで 1 つのワーカー アカウントが使用されます。

ワーカー アカウントは、他のワーカー アカウントによって使用されるファイルを、読み取ったり操作したりすることはできません。
 
コンピューターの管理者であれば、各プロセスによって作成されたディレクトリを表示できます。 各ディレクトリはセッション GUID によって識別されます。

## <a name="see-also"></a>参照

[SQL Server の機械学習のアーキテクチャの概要](../../advanced-analytics/r/architecture-overview-sql-server-r.md)
