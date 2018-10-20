---
title: SQL Server machine learning 用のセキュリティ |Microsoft Docs
description: SQL Server Machine Learning Services の機能拡張フレームワークのセキュリティの概要。 ログインとユーザー アカウント、SQL Server スタート パッド サービス、複数のスクリプト、およびファイルのアクセス許可を実行しているワーカー アカウントのセキュリティ。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a5d109e16c81481f9e4267dc4963ecea74cfa736
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419377"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services の機能拡張フレームワークのセキュリティの概要

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機能拡張フレームワークと、SQL Server データベース エンジンと関連コンポーネントを統合するために使用される全体的なセキュリティ アーキテクチャについて説明します。 セキュリティ保護可能なサービス、プロセスの id およびアクセス許可を確認します。 主要な概念と SQL Server の機能拡張のコンポーネントの詳細については、次を参照してください。 [SQL Server Machine Learning Services で拡張可能アーキテクチャ](extensibility-framework.md)]。

## <a name="securables-for-external-script"></a>外部スクリプトのセキュリティ保護可能な

R または Python で記述された外部スクリプトがへの入力パラメーターとして送信された、[システム ストアド プロシージャ](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、この目的用に作成または定義したストアド プロシージャにラップされています。 また、事前トレーニング済みおよび t-sql の呼び出し可能なデータベースのテーブルのバイナリ形式で格納するモデルがあります[PREDICT](../../t-sql/queries/predict-transact-sql.md)関数。

スクリプトは、既存のデータベース スキーマ オブジェクト、ストアド プロシージャおよびテーブルを通じて提供されるため、ある新しい[セキュリティ保護可能な](../../relational-databases/security/securables.md)の SQL Server Machine Learning サービス。

スクリプトを使用している方法やので構成するに関係なくは、データベース オブジェクトが作成され、保存可能性がありますが、スクリプトを格納する新しいオブジェクトの種類が導入されたありません。 その結果を使用する機能を作成するし、データベースの保存、オブジェクトが、ユーザーに対して既に定義されているデータベースのアクセス許可に大きく依存します。

<a name="permissions"></a>

## <a name="permissions"></a>アクセス許可

データベース ログインおよびロールの SQL Server のデータのセキュリティ モデルは、R と Python スクリプトを拡張します。 SQL Server のデータを使用するか、計算コンテキストとして SQL Server を実行する外部のスクリプトを実行するには、SQL Server ログインまたは Windows ユーザー アカウントが必要です。 アドホック クエリを実行する権限を持つデータベース ユーザーは、同じデータを R または Python スクリプトからアクセスできます。

ログインまたはユーザー アカウントを識別、*セキュリティ プリンシパル*、複数レベルの外部スクリプトの要件に応じて、アクセスする必要があります。

+ 外部スクリプトが有効になっているデータベースにアクセスする権限です。
+ テーブルなどのセキュリティで保護されたオブジェクトからデータを読み取るアクセス許可。
+ モデルをスコア付けの結果など、テーブルに新しいデータを書き込む権限です。
+ テーブルなどの新しいオブジェクトを作成する機能には、外部のスクリプトを使用するプロシージャが格納されているか、カスタム関数を使用して R または Python ジョブ。
+ SQL Server コンピューターでは、新しいパッケージをインストールまたはユーザーのグループに提供されるパッケージを使用する権限。

実行コンテキストとして SQL Server を使用して外部スクリプトを実行する各ユーザーは、データベース内のユーザーにマップする必要があります。 個別にデータベース ユーザー アクセス許可を設定ではなく、アクセス許可のセットを管理し、これらのロールにユーザーの割り当てではなくユーザーのアクセス許可を個別に設定するロールを作成できます。

詳細については、次を参照してください。 [SQL Server Machine Learning サービスへのアクセス許可をユーザーに付与](../../advanced-analytics/security/user-permission.md)します。

## <a name="permissions-when-using-an-external-client-tool"></a>外部のクライアント ツールを使用する場合のアクセス許可

外部のクライアント ツールで R または Python を使用しているユーザーは、ログインや、外部スクリプト (データベース内)、または access データベース オブジェクトとデータを実行する必要がある場合は、データベース内のユーザーにマップされているアカウントが必要です。 同じアクセス許可は、外部のスクリプトをリモート データ サイエンス クライアントから送信するかどうかが必要ですか、T-SQL ストアド プロシージャを使用してを実行します。

たとえば、ローカル コンピューターで実行されている外部スクリプトを作成して、SQL Server でそのスクリプトを実行します。 次の条件が満たされていることを確認する必要があります。

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

<a name="launchpad"></a>

## <a name="services-used-in-external-processing-launchpad"></a>外部の処理 (スタート パッド) で使用されるサービス

機能拡張フレームワークを 1 つの新しい NT サービスの追加、[サービスの一覧](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md#Service_Details)SQL Server のインストール: [ **SQL Server スタート パッド (MSSSQLSERVER)**](extensibility-framework.md#launchpad)。

データベース エンジンでは、SQL Server スタート パッド サービスを使用して、別のプロセスとして、R または Python のセッションをインスタンス化します。 低い特権のアカウントの下で、プロセスが実行されます。SQL Server、スタート パッド、およびストアド プロシージャまたはホストのクエリが実行されたときのユーザー id とは異なります。 R と SQL Server での Python のセキュリティと分離のモデルの基になる低い特権のアカウントで別のプロセスでスクリプトを実行します。

外部プロセスを起動するだけでなく、スタート パッドは、呼び出し元のユーザーの id を追跡して、プロセスを開始するために使用する低特権ワーカー アカウントにその id のマッピングを行うはも。 スクリプトまたはコードを呼び出して SQL Server のデータと操作、一部のシナリオでは、スタート パッドは通常の id の転送をシームレスに管理できます。 SELECT ステートメントを格納しているか、関数およびその他のプログラミング オブジェクトを呼び出すスクリプトは通常、呼び出し元のユーザーに十分なアクセス許可がある場合に成功します。

> [!NOTE]
> 既定では、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]が実行するように構成されている**NT service \mssqllaunchpad**、外部スクリプトを実行するすべての必要なアクセス許可がプロビジョニングされていますが。 構成可能なオプションの詳細については、次を参照してください。 [SQL Server スタート パッド サービスの構成](../security/sql-server-launchpad-service-account.md)します。

<a name="sqlrusergroup"></a>

## <a name="identities-used-in-processing-sqlrusergroup"></a>(SQLRUserGroup) の処理に使用される id

**SQLRUserGroup** (SQL 制限対象のユーザー グループ) は、SQL Server セットアップによって作成され、低い特権のローカル Windows ユーザー アカウントのプールが含まれています。 外部プロセスが必要なときにスタート パッド、使用可能なワーカー アカウントを使用して、プロセスを実行します。 具体的には、スタート パッドは、使用可能なワーカー アカウントをアクティブに、呼び出し元のユーザーの id にマップし、ワーカー アカウントで、スクリプトを実行します。

+ **SQLRUserGroup**特定のインスタンスにリンクさせます。 ラーニングの有効にするコンピューターのインスタンスごとに、独立したプールのワーカー アカウントが必要です。 インスタンス間でアカウントを共有することはできません。

+ ユーザー アカウント プールのサイズは静的であり、既定値は 20、20 の同時セッションをサポートします。 同時に起動できる外部のランタイム セッションの数は、このユーザー アカウント プールのサイズによって制限されます。 

+ プールのワーカー アカウント名は、sqlinstancename*nn*します。 たとえば、既定のインスタンスで**SQLRUserGroup**という名前に、最大 MSSQLSERVER20 MSSQLSERVER01、MSSQLSERVER02 などのアカウントが含まれています。

並列化されたタスクでは、追加のアカウントは使用しません。 たとえば、ユーザーは、並列処理を使用するスコア付けのタスクを実行する場合のすべてのスレッドと同じワーカー アカウントが再利用されます。 Machine learning の頻繁に使用する場合は、外部スクリプトの実行に使用するアカウントの数を増やすことができます。 詳細については、次を参照してください。 [machine learning のユーザー アカウント プールを変更する](../../advanced-analytics/administration/modify-user-account-pool.md)します。

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>SQL Server 2019 で AppContainer の分離

SQL Server の 2019 のセットアップは作成されなくなりましたのワーカー アカウント**SQLRUserGroup**します。 によって分離を実現する代わりに、 [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation)します。 ストアド プロシージャまたはクエリの外部のスクリプトが検出された場合、実行時に、SQL Server は、要求で拡張機能に固有の起動ツールのスタート パッドを呼び出します。 スタート パッドは、その id でのプロセスで適切なランタイム環境を呼び出し、そのを含む、AppContainer をインスタンス化します。 ローカル アカウントとパスワードの管理が必要になるために、この変更の使用をお勧めします。 また、ローカル ユーザー アカウントは禁止されている、インストールでローカル ユーザー アカウントの依存関係をなくすこと、この機能を使用するようになりました。

、SQL Server で実装された AppContainers は、内部のメカニズムです。 プロセス モニターで AppContainers の物理的な証拠が表示されなくなります、中には、プロセスがネットワーク呼び出しを行うことを防ぐためにセットアップによって作成された送信ファイアウォール規則で見つけることができます。 詳細については、次を参照してください。 [SQL Server Machine Learning サービスのファイアウォールの構成](../../advanced-analytics/security/firewall-configuration.md)します。

> [!Note]
> SQL Server の 2019 で**SQLRUserGroup**は 1 つのメンバーが複数のワーカー アカウントではなく、1 つの SQL Server スタート パッド サービス アカウントになっています。
::: moniker-end

### <a name="permissions-granted-to-sqlrusergroup"></a>SQLRUserGroup に与えられた権限

既定のメンバーで**SQLRUserGroup**読み取りし、実行アクセス許可の SQL Server 内のファイルに**Binn**、 **R_SERVICES**、および**PYTHON_SERVICES**ディレクトリ、実行可能ファイル、ライブラリ、および SQL Server と共にインストールされる R と Python のディストリビューションでは組み込みのデータセットにアクセスします。 

SQL Server 上の機密リソースを保護する、アクセスを拒否するアクセス制御リスト (ACL) を定義することができます必要に応じて**SQLRUserGroup**します。 逆に、SQL Server 自体とは別のホスト コンピューター上に存在するローカル データ リソースへのアクセス許可を付与することもできます。 

仕様上、 **SQLRUserGroup**はデータベース ログインまたは任意のデータへのアクセス許可がありません。 特定の状況で信頼できる Windows id が呼び出し元のユーザーの場合に特にループ バックの接続を許可するログインを作成する場合があります。 この機能が呼び出されます[*暗黙の認証*](#implied-authentication)します。 詳細については、次を参照してください。[データベース ユーザーとしての SQLRUserGroup の追加](../../advanced-analytics/security/add-sqlrusergroup-to-database.md)します。

## <a name="identity-mapping"></a>Id マッピング

セッションが開始されると、スタート パッドは、ワーカー アカウントへの呼び出し元のユーザー id をマップします。 外部の Windows ユーザーまたはワーカー アカウントの有効な SQL ログインのマッピングでは、外部のスクリプトを実行する SQL の有効期間はストアド プロシージャに対してのみ有効です。 同じログインからの並列クエリは、同じユーザー ワーカー アカウントにマップされます。

実行中には、スタート パッドは、セッションの終了時に削除するセッション データを格納する一時フォルダーで作成します。 ディレクトリは、アクセスを制限します。 R、RLauncher が、このタスクを実行します。 Python の場合は、PythonLauncher は、このタスクを実行します。 個々 のワーカー アカウントごとでは、独自のフォルダーには制限され、独自のレベル上にあるフォルダー内のファイルにアクセスできません。 ただし、ワーカー アカウントは読み取り、書き込み、または作成されたセッション作業フォルダーの下の子を削除します。 コンピューターの管理者であれば、各プロセスによって作成されたディレクトリを表示できます。 各ディレクトリはセッション GUID によって識別されます。

<a name="implied-authentication"></a>

## <a name="implied-authentication-loop-back-requests"></a>暗黙の認証 (ループ バック要求)

*暗黙の認証*に SQL Server に低い特権のワーカー アカウントを信頼されたユーザー id として示されるように実行されている外部のプロセスがデータや操作の要求をバックをループする接続要求の動作について説明します。 概念としては、暗黙の認証は、R または Python スクリプトなどの外部プロセスからの要求で、信頼関係接続を指定する SQL Server 接続文字列での Windows 認証に固有です。 としてもに指す、*にループに戻って*します。

信頼関係接続では、追加の構成にのみ、R と Python のスクリプトから実行可能なです。 機能拡張のアーキテクチャで、R と Python のプロセスがワーカー アカウント、アクセス許可を親から継承で実行**SQLRUserGroup**します。 接続文字列を指定すると`Trusted_Connection=True`、接続要求では、既定では SQL Server に既知でないワーカー アカウントの id が表示されます。

信頼関係接続を成功させるにはデータベース ログインを作成する必要があります、 **SQLRUserGroup**します。 その後、すべての信頼済みのすべてのメンバーからの接続**SQLRUserGroup** SQL Server ログイン権限があります。 手順については、次を参照してください。[データベース ログインを追加の SQLRUserGroup](../../advanced-analytics/security/add-sqlrusergroup-to-database.md)します。

信頼された接続は、接続要求の最も広く使用されている構成ではできません。 R または Python スクリプトでは、接続を指定する場合、ODBC データ ソースへの接続だ場合に、SQL ログインまたは完全に指定されたユーザー名とパスワードを使用する方が一般的になります。

### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>R と Python のセッションの暗黙的などの認証のしくみ

次の図は、R ランタイムは R 向けの暗黙の認証と SQL Server コンポーネントの相互作用を示しています。

![R の暗黙の認証](../security/media/implied-auth-rsql.png)

次の図は、Python ランタイムは Python の暗黙の認証と SQL Server コンポーネントの相互作用を示しています。

![Python の暗黙の認証](../security/media/implied-auth-python2.png)

## <a name="no-support-for-transparent-data-encryption-at-rest"></a>Transparent Data Encryption は保存時のサポートはされていません

[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)送信または受信外部スクリプトのランタイムからのデータはサポートされていません。 理由は、SQL Server プロセスの外部 (R または Python) は、外部プロセスを実行します。 そのため、外部ランタイムで使用されるデータは、データベース エンジンの暗号化機能によって保護されていません。 この動作は、データベースからデータを読み取り、コピーを作成する SQL Server コンピューターで実行されているその他のクライアントと違いはありません。

その結果、TDE**ない**または任意の保存された中間結果をディスクに保存されるデータまたは R または Python のスクリプトで使用するすべてのデータに適用します。 ただし、他の種類の暗号化など、ファイルまたはフォルダー レベルで Windows の BitLocker 暗号化またはサード パーティ製の暗号化の適用も適用されます。

場合に[Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)、外部ランタイムには、暗号化キーへのアクセス権はありません。 そのため、スクリプトにデータを送信できません。

## <a name="next-steps"></a>次の手順

この記事では、コンポーネントを説明しに組み込まれたセキュリティ アーキテクチャの対話モデル、[拡張性フレームワーク](../../advanced-analytics/concepts/extensibility-framework.md)します。 この記事で説明したポイントには、R、Python、およびユーザー id がワーカー アカウントにマップする方法のプロセスの分離、スタート パッドの SQLRUserGroup、ワーカー アカウントの目的が含まれます。 

次の手順の手順を確認[アクセス許可を与える](../../advanced-analytics/security/user-permission.md)します。 Windows 認証を使用するサーバーも参照してください[データベース ログインを追加の SQLRUserGroup](../../advanced-analytics/security/add-sqlrusergroup-to-database.md)に追加の構成が必要な場合について説明します。