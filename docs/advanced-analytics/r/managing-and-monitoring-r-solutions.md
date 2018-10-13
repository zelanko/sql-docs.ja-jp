---
title: 管理し、SQL server machine learning ワークロードの統合 |Microsoft Docs
description: SQL Server のデータベース管理者として、machine learning のデータベース エンジンのインスタンス上の R と Python のサブシステムの展開の管理タスクを確認します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c921b89dc3f6928ccbfc3f9fc727015dadc05b7b
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169082"
---
# <a name="manage-and-integrate-machine-learning-workloads-on-sql-server"></a>管理し、SQL server machine learning ワークロードの統合
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、複数のワークロードをサポートしているサーバー資産に効率的なデータ サイエンス インフラストラクチャのデプロイを担当する SQL Server データベース管理者向けです。 R の管理に関連する管理上の問題領域をフレームし、Python のコードは SQL Server で実行します。 

## <a name="what-is-feature-integration"></a>新機能と機能の統合

R と Python の機械学習がによって提供される[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)データベース エンジンのインスタンスに拡張機能として。 統合は、主にセキュリティ レイヤーと次のとおり、データ定義言語では。

+ ストアド プロシージャに R をそのまま使用する機能が装備されてと Python コードの入力パラメーターとして。 開発者やデータ サイエンティストが使用できる、[システム ストアド プロシージャ](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql?view=sql-server-2017)か、コードをラップするカスタム プロシージャを作成します。
+ T-SQL 関数 (つまり、 [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)) 以前にトレーニングしたデータ モデルを利用することができます。 この機能は、T-SQL を使用します。 そのためがない具体的には、機械学習の拡張機能がインストールされているシステム上で呼び出すことができます。
+ 既存のデータベース ログインとロール ベースのアクセス許可には、同じデータを利用するユーザーが起動スクリプトがについて説明します。 一般的な規則として、クエリ、データにアクセスできない場合にアクセスできませんが、スクリプトか。

## <a name="feature-availability"></a>利用可能な機能

R と Python の統合には、一連の手順で使用できるになります。 1 つ目は、セットアップ、する[を含めるか、追加、 **Machine Learning サービス**](../install/sql-machine-learning-services-windows-install.md)データベース エンジンのインスタンスに機能します。 後続の手順としては、(既定ではオフ)、データベース エンジン インスタンスに対する外部のスクリプトを有効にする必要があります。

この時点では、データベース管理者だけでは、作成、外部スクリプトを実行し、追加、または、パッケージを削除する完全な権限を持っているし、ストアド プロシージャ、およびその他のオブジェクトを作成します。

その他のすべてのユーザーに EXECUTE ANY EXTERNAL SCRIPT 権限を付与する必要があります。 追加[標準的なデータベース アクセス許可](../security/user-permission.md)できるか判断するかどうかユーザー オブジェクトを作成、スクリプトを実行する、シリアル化とトレーニング済みのモデルを使用し、などです。 

## <a name="resource-allocation"></a>リソース割り当て

ストアド プロシージャと外部の処理の呼び出しの T-SQL クエリは、既定のリソース プールに使用可能なリソースを使用します。 既定の構成の一環として、R と Python のセッションなどの外部プロセスは、ホスト システムでメモリの合計の最大 20% が許可されます。 

リソースの割り当てを再調整する場合は、そのシステムで実行されているマシン ラーニング ワークロードに対応する影響で、既定のプールを変更できます。

別のオプションでは、特定のプログラム、ホスト、または特定の時間間隔中に発生したアクティビティから送信されたセッションをキャプチャするカスタムの外部リソース プールを作成します。 詳細については、次を参照してください。 [R および Python 実行のためのリソース レベルを変更するリソース ガバナンス](../administration/resource-governance.md)と[リソース プールを作成する方法](../administration/how-to-create-a-resource-pool.md)詳しい手順についてはします。

## <a name="isolation-and-containment"></a>分離およびコンテインメント

処理アーキテクチャは、コア エンジンの処理から外部のスクリプトを分離する設計されています。 R と Python スクリプトは、ローカルのワーカー アカウントの下の個別のプロセスとして実行します。 タスク マネージャーでは、プロセスを監視できます R と Python、SQL Server のサービス アカウントの異なる特権の低いローカル ユーザー アカウントで実行します。 

個々 の低特権アカウントで R と Python のプロセスを実行すると、次の利点があります。

+ コア データベース操作の影響を与えずに、R または Python のプロセスを終了する R と Python のセッションからのコア エンジンのプロセスを分離します。 

+ ホスト コンピューター上の外部スクリプトのランタイム プロセスの特権が減少します。

最小特権のアカウントがセットアップ中に作成され、Windows で*ユーザー アカウント プール*と呼ばれる**SQLRUserGroup**します。 既定では、R と SQL Server での Python のプログラム フォルダーで実行可能ファイル、ライブラリ、および組み込みのデータセットを使用するアクセス許可を持ちます。 

Dba では、SQL Server データのセキュリティを使用するには、スクリプトを実行する権限を持っているユーザーを指定して、ジョブで使用されるデータは同じを制御するセキュリティ ロールの下で管理されていることに T-SQL クエリを通じてアクセスします。 システム管理者は、明示的に拒否できます**SQLRUserGroup** Acl を作成してローカル サーバー上の機密データにアクセスします。

>[!NOTE]
> 既定で、 **SQLRUserGroup**が、ログインまたはアクセス許可では、SQL Server 自体。 ワーカー アカウントがデータ アクセスのログインを要求する必要があります、する必要があります、手動で作成します。 具体的には、ログインの作成を呼び出すシナリオは、ユーザー id が Windows ユーザーと信頼されたユーザーを指定する接続文字列のデータや、データベース エンジン インスタンスに対する操作の実行でスクリプトからの要求をサポートするためにです。 詳細については、次を参照してください。[データベース ユーザーとしての SQLRUserGroup の追加](../../advanced-analytics/security/add-sqlrusergroup-to-database.md)します。

## <a name="disable-script-execution"></a>スクリプトの実行を無効にします。

ランナウェイのスクリプトが発生した場合に以前、最初に、外部スクリプトの実行を有効にするために行う手順を逆すべてスクリプトの実行を禁止できます。

1. SQL Server Management Studio または他のクエリ ツールでは、設定するには、このコマンドを実行`external scripts enabled`0 または FALSE にします。

    ```sql
    EXEC sp_configure  'external scripts enabled', 0
    RECONFIGURE WITH OVERRIDE
    ```
2. データベース エンジン サービスを再起動します。

この問題を解決した後は、R を再開して、データベース エンジン インスタンスに対する Python スクリプトをサポートする場合、インスタンス上のスクリプトの実行を再度有効に注意してください。 詳細については、次を参照してください[スクリプトの実行を有効にする。](../install/sql-machine-learning-services-windows-install.md#enable-script-execution)

## <a name="extend-functionality"></a>機能を拡張します。

多くの場合、データ サイエンスには、パッケージの展開と管理のための新しい要件が導入されています。 データ サイエンティストの場合は、カスタム ソリューションでのオープン ソースおよびサード パーティ製のパッケージを利用する一般的なプラクティスを勧めします。 他のパッケージに依存関係パッケージの一部が、この場合は、評価して、目標に到達する複数のパッケージをインストールする必要があります。

サーバー資産の責任の dba 実稼働サーバー上に任意の R と Python パッケージの配置は未知のチャレンジを表します。 パッケージを追加する前に、外部のパッケージで提供される機能がないと等価の組み込みに本当に必要なかどうかを評価する必要があります[R 言語](r-libraries-and-data-types.md)と[Python ライブラリ](../python/python-libraries-and-data-types.md)インストールSQL Server のセットアップ。 

代替サーバー パッケージのインストール方法としては、データ サイエンティストでにできる可能性があります[ビルドし、外部のワークステーションでソリューションを実行](../r/set-up-a-data-science-client.md)、SQL Server からデータを取得するが、すべての分析でワークステーションをローカルで実行代わりに、サーバー自体にします。 

外部ライブラリ関数が必要なし、サーバー操作やデータ全体のリスクを引き起こすことはありませんを後で判断した場合は、パッケージを追加する複数の方法論から選択することができます。 ほとんどの場合は、SQL Server にパッケージを追加する管理者権限が必要です。 詳細についてを参照してください。 [SQL Server での Python のインストール パッケージ](../python/install-additional-python-packages-on-sql-server.md)と[SQL Server で R のインストール パッケージ](install-additional-r-packages-on-sql-server.md)します。

> [!NOTE]
> R パッケージの代替メソッドを使用する場合は、サーバー管理者権限はパッケージのインストールの具体的には必要ありません。 参照してください[SQL Server で R のインストール パッケージ](install-additional-r-packages-on-sql-server.md)詳細についてはします。

## <a name="next-steps"></a>次の手順

+ 概念とコンポーネントの確認、[拡張可能アーキテクチャ](../concepts/extensibility-framework.md)と[セキュリティ](../concepts/security.md)背景情報についてはします。

+ 機能のインストールの一環として、既に使い慣れていたかもしれないとエンド ユーザー データのアクセス制御がない場合を参照してください[SQL Server machine learning のユーザーのアクセス許可を付与](../security/user-permission.md)詳細についてはします。 

+ 計算処理を要する機械学習のワークロードのシステム リソースを調整する方法について説明します。 詳細については、次を参照してください。[リソース プールを作成する方法](../administration/how-to-create-a-resource-pool.md)します。
