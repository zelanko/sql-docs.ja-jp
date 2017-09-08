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
ms.openlocfilehash: 8388d7c9d22a49a49a1a45a6fa6b479107f9ccae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="security-overview-sql-server-r-services"></a>セキュリティの概要 (SQL Server R サービス)

ここでは、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データベース エンジンおよび関連するコンポーネントを R ランタイムに接続するために使用される全体的なセキュリティ アーキテクチャについて説明します。 セキュリティ プロセスの例は、エンタープライズ環境で R を使用する一般的な次の 2 つのシナリオのために提供されます。

+ データ サイエンス クライアントから [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で RevoScaleR 関数 を実行
+ ストアド プロシージャを使用して R を [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] から直接実行

## <a name="security-overview"></a>セキュリティの概要

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL Server のデータを使用するか、計算コンテキストとして SQL Server を実行する R スクリプトを実行するログインまたは Windows ユーザー アカウントが必要です。 この要件は、両方に適用されます。[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]および SQL Server 2017 Machine Learning Services です。 

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

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] セキュリティとスタート パッド セキュリティの相互作用

R スクリプトが [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターのコンテキストで実行されるとき、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスは、外部プロセス用に確立されたワーカー アカウントのプールから使用可能なワーカー アカウント (ローカル ユーザー アカウント) を取得し、そのワーカー アカウントを使用して関連するタスクを実行します。 

たとえば、自分の Windows ドメイン資格情報で R ジョブを開始すると、そのアカウントがスタート パッドのワーカー アカウント *SQLRUser01* にマップされることがあります。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] は、ワーカー アカウントへのマッピングの後で、プロセスの開始に使用されるユーザー トークンを作成します。 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のすべての処理が完了すると、ユーザー ワーカー アカウントは空きとしてマークされ、プールに返されます。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] について詳しくは、「[New Components in SQL Server to Support R Integration](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md)」(R 統合をサポートする SQL Server の新コンポーネント) をご覧ください。

> [!NOTE]
スタート パッドでワーカー アカウントを管理して R ジョブを実行するには、ワーカー アカウントを含むグループ SQLRUserGroup が [ローカル ログオンを許可する] アクセス許可を持つ必要があります。このアクセス許可がない場合、R Services は機能しないことがあります。 既定ではこのアクセス許可はすべての新規ローカル ユーザーに付与されますが、組織によっては、ワーカー アカウントが SQL Server に接続して R ジョブを実行できないように厳しいグループ ポリシーが実施される可能性があります。  

## <a name="security-of-worker-accounts"></a>ワーカー アカウントのセキュリティ

外部の Windows ユーザーまたはワーカー アカウントに有効な SQL ログインのマッピングは、R スクリプトを実行する SQL クエリの有効期間の有効期間にのみ有効です。 

同じログインからの並列クエリは、同じユーザー ワーカー アカウントにマップされます。

プロセスで使用されるディレクトリは、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] が RLauncher を使用して管理します。ディレクトリへのアクセスは制限されます。 ワーカー アカウントは、自分のフォルダーよりも上にあるフォルダー内のファイルにはアクセスできません。ただし、R スクリプトを含む SQL クエリのために作成されたセッション作業フォルダー内の子ファイルの読み取り、書き込み、削除は行うことができます。

ワーカー アカウントの数、アカウント名、またはアカウント パスワードを変更する方法について詳しくは、「[Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)」(SQL Server R Services のユーザー アカウント プールの変更) を参照してください。


## <a name="security-isolation-for-multiple-external-scripts"></a>複数外部スクリプトでのセキュリティ分離

分離メカニズムは物理ユーザー アカウントに基づいています。 サテライト プロセスは特定の言語ラインタイムに対して開始されるため、各サテライト タスクは [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] によって指定されたワーカー アカウントを使用します。 タスクが複数のサテライトを必要とする場合 (たとえば並列クエリなど)、関連するすべてのタスクで 1 つのワーカー アカウントが使用されます。

ワーカー アカウントは、他のワーカー アカウントによって使用されるファイルを、読み取ったり操作したりすることはできません。
 
コンピューターの管理者であれば、各プロセスによって作成されたディレクトリを表示できます。 各ディレクトリはセッション GUID によって識別されます。

## <a name="see-also"></a>参照
[アーキテクチャの概要](../../advanced-analytics/r-services/architecture-overview-sql-server-r.md)

