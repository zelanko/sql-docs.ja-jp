---
title: "セキュリティの概要 (SQL Server R サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# セキュリティの概要 (SQL Server R サービス)

このトピックの接続に使用される全体的なセキュリティ アーキテクチャについて説明します [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データベース エンジンと R ランタイムに関連するコンポーネントです。 エンタープライズ環境で R を使用するための 2 つの一般的なシナリオについては、セキュリティ プロセスの例が用意されています。

+ RevoScaleR 関数を実行する [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データ サイエンスのクライアントから
+ R から直接実行している [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ストアド プロシージャの使用

## セキュリティの概要

A [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ログインまたは Windows ユーザー アカウントが使用するすべての R のジョブの実行に必要な [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]です。 ログインまたはユーザー アカウントを識別、 *セキュリティ プリンシパル*, 、R が実行されるデータベースにアクセスする権限だけでなくテーブルなどのセキュリティで保護されたオブジェクトからデータを読み取るか、新しいデータを書き込んだり、R のジョブで必要な場合は、新しいオブジェクトを追加するアクセス許可を持つ必要があります。

したがって、厳密な要件を R コードを実行する各ユーザーに対して [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] そのコードの RevoScaleR 関数を使用してリモート データ サイエンス クライアントから送信されるかどうかや、T-SQL ストアド プロシージャを使用して開始に関係なく、データベースのログインにマップする必要があります。 

たとえば、ラップトップで実行されるいくつかの R コードが作成され、そのコードが実行している [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。 次の条件を満たしていることを確認してする必要があります。

+ データベースは、リモート接続を許可します。
+ 名前と、R コードで使用したパスワードで SQL ログインが追加されて、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンス レベルでします。 または、インスタンス上のユーザーとして接続文字列で指定された Windows ユーザーを追加する必要があります Windows 統合認証を使用している場合。
+ SQL ログインまたは Windows ユーザーでは、外部スクリプトを実行する権限が付与する必要があります。 一般に、このアクセス許可は、データベース管理者によってのみ追加できます。
+ SQL ログインまたはウィンドウのユーザーは、R のジョブを実行してこれらの操作のいずれかの各データベース内の適切な権限を持つユーザーとして追加する必要があります。
    + データを取得します。
    + 作成やデータの更新 
    + テーブルやストアド プロシージャなどの新しいオブジェクトを作成します。

ログインまたは Windows ユーザー アカウントのプロビジョニングおよびために必要なアクセス許可が付与されたが後で、R コードを実行できます [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] R のデータ ソース オブジェクトを使用して、またはストアド プロシージャを呼び出すことによってです。 R はから起動されるたびに [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 、データベース エンジンのセキュリティは、R のジョブを開始し、ユーザーまたはセキュリティ保護可能なオブジェクトへのログインのマッピングを管理するユーザーのセキュリティ コンテキストを取得します。 

そのため、リモート クライアントから開始するすべての R のジョブでは、接続文字列の一部としてログインまたはユーザーの情報を指定する必要があります。


## 相互作用 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] セキュリティとスタート パッドのセキュリティ

コンテキストでの R スクリプトの実行時に、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 、コンピューター、 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスが外部プロセス用に確立されたワーカー アカウントのプールから使用可能なワーカー アカウント (ローカル ユーザー アカウント) を取得し、そのワーカー アカウントを使用して、関連するタスクを実行します。 

たとえば、Windows ドメインの資格情報で、R のジョブを開始する場合、アカウントがありますにマップするスタート パッドのワーカー アカウント *SQLRUser01*です。

ワーカー アカウントへのマッピング後 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] プロセスを開始するために使用するユーザー トークンを作成します。 

ときにすべて [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 操作が完了し、ユーザー ワーカー アカウントを空きとしてマークされているし、プールに返されます。

詳細については [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], を参照してください [R の統合をサポートする SQL Server の新しいコンポーネント](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)します。

## 作業者のアカウントのセキュリティ
外部の Windows ユーザーまたはワーカー アカウントに有効な SQL ログインには、このマッピングは、R スクリプトを実行する SQL クエリの有効期間の有効期間中にのみ有効です。 

同じログインから並列クエリは、ワーカーと同じユーザー アカウントにマップされます。

プロセス用に使用されるディレクトリを管理している、 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] RLauncher を使用してディレクトリは、アクセスが制限されたとします。 ワーカー アカウントが、それ自体の上のフォルダー内のファイルにアクセスできませんが、読み取り、書き込み、または R スクリプトの SQL クエリを作成したセッションの作業フォルダーの下の子を削除できます。

ワーカー アカウント、アカウント名、またはアカウントのパスワードの数を変更する方法の詳細については、次を参照してください。 [SQL Server の R のサービスのユーザー アカウントのプールを変更](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)です。


## 複数の外部スクリプトのセキュリティの分離

分離メカニズムは、物理的なユーザー アカウントに基づいています。 各サテライト タスクを特定の言語の実行時に、サテライト プロセスが開始されるとようで指定されたワーカー アカウントを使用して、 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]です。 タスクは、複数のサテライトを必要とする場合など、並列クエリの場合、1 つのワーカー アカウントは使用のすべての関連するタスクされます。

ワーカー アカウントを参照してくださいしたり、他の作業者のアカウントで使用されるファイルを操作することができません。
 
コンピューターの管理者の場合は、プロセスごとに作成されたディレクトリを表示できます。 各ディレクトリは、そのセッション GUID によって識別されます。

## 参照
[アーキテクチャの概要](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)