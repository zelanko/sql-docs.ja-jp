---
title: 機械学習で SQL Server のセキュリティに関する考慮事項 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c8aa787088873adff5256208636063ba6f59b8b6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203724"
---
# <a name="security-considerations-for-machine-learning-in-sql-server"></a>機械学習で SQL Server のセキュリティに関する考慮事項
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、管理者や設計者は、留意ください machine learning のサービスを使用する場合に、セキュリティの考慮事項を一覧表示します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="use-a-firewall-to-restrict-network-access"></a>ネットワーク アクセスを制限するのにファイアウォールを使用します。

既定のインストールで Windows ファイアウォール ルールが使用する外部のランタイム プロセスからのすべての発信ネットワーク アクセスをブロックします。 パッケージをダウンロードすると、悪意のある可能性があるその他のネットワーク呼び出しからは、外部のランタイム プロセスを防ぐためにファイアウォール ルールを作成する必要があります。

別のファイアウォール プログラムを使用している場合は、ローカル ユーザー アカウントまたはユーザー アカウント プールによって表されるグループ用のルールを設定して、外部のランタイムの送信ネットワーク接続をブロックする規則を作成することもできます。

R、または Python ランタイムで無制限のネットワーク アクセスを防ぐために Windows ファイアウォール (または別のファイアウォール) を有効にすることを強くお勧めします。

## <a name="authentication-methods-supported-for-remote-compute-contexts"></a>リモート計算コンテキストでサポートされる認証メソッド

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 間の接続を作成するときに、Windows 統合認証と SQL の両方のログインをサポートしている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とリモート データ サイエンス クライアント。

たとえば、ラップトップ コンピューターで R ソリューションを開発しており、SQL Server コンピューターに対して計算を実行するとします。 使用して、R で SQL Server データ ソースを作成すると、 **rx**関数との接続文字列を定義する、Windows 資格情報に基づいています。

変更すると、_計算コンテキスト_Windows アカウントに必要なアクセス許可がある場合は、すべての R コードを SQL Server コンピューターで実行するよう、SQL Server コンピューターにラップトップからです。 さらに、R コードの一部として実行された SQL クエリは、管理者の資格情報も実行されます。

このシナリオでは、SQL ログインの使用はサポートされてもします。 ただし、これは混合モード認証を許可する SQL Server インスタンスを構成することが必要です。

### <a name="implied-authentication"></a>暗黙の認証

 一般に、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]外部スクリプトの実行時を起動し、独自のアカウント下でスクリプトを実行します。 ただし、外部のランタイムは、ODBC 呼び出しを行う場合、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ODBC 呼び出しが異常終了しないようにするコマンドを送信したユーザーの資格情報の権限を借用します。 これは*暗黙の認証*と呼ばれます。
 
 > [!IMPORTANT]
 > 暗黙の認証には、Windows ユーザー アカウントを含むグループ、ワーカーの成功 (既定では、 **SQLRUserGroup**)、インスタンス、およびこのアカウントがへのアクセス許可を付与する必要がありますの master データベースにアカウントが必要インスタンスに接続します。
 > 
 > グループ**SQLRUserGroup** Python スクリプトを実行しているときにも使用します。 

一般に、なくすることより大規模なデータセットを事前に SQL Server に移動 RODBC または別のライブラリを使用してデータを読み取るしようとしています。 お勧めします。 また、SQL Server クエリまたはビュー、プライマリ データ ソースとして使用、パフォーマンス向上のためです。 

たとえば、SQL サーバーから、トレーニング データ (通常、最大のデータ) を取得し、外部ソースからの要因の一覧を取得する可能性があります。 ほとんどの ODBC データ ソースからデータを取得するリンク サーバーを定義することができます。 詳細については、次を参照してください。[リンク サーバーを作成](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine)です。

外部データ ソースへの ODBC 呼び出しへの依存関係を最小限に抑えるに可能性がありますも個別のプロセスとしてデータ エンジニア リングを実行およびテーブルの結果を保存または T-SQL を使用します。 SQL の vs でのデータ エンジニア リングの良い例は、このチュートリアルを参照してください。R: [T-SQL を使用してデータの機能を作成する](../tutorials/sqldev-create-data-features-using-t-sql.md)です。

## <a name="no-support-for-encryption-at-rest"></a>保存時の暗号化はサポートされていません

[Transparent Data Encryption (TDE)](https://docs.microsoft.com/sql/relational-databases/security/encryption/transparent-data-encryption)に送信するか、外部スクリプトの実行時から受信したデータはサポートされていません。 その理由は、SQL Server のプロセスの外部 R (または Python) を実行します。したがって、外部のランタイムによって使用されるデータは、暗号化、データベース エンジンの機能では保護されません。  この動作は、データベースからデータを読み取り、コピーを作成する SQL Server コンピューターで実行されているその他のクライアントと違いはありません。

その結果、TDE**は**R または Python のスクリプトで使用するすべてのデータまたは永続化された中間結果をディスクに保存されるデータに適用します。 ただし、他の種類の暗号化など、ファイルまたはフォルダー レベルで、Windows BitLocker 暗号化またはサード パーティ製の暗号化の適用を引き続き適用されます。

場合、 [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/overview-of-key-management-for-always-encrypted)、外部のランタイムには、暗号化キーへのアクセスはありません。 スクリプトにそのため、データを送信できません。

## <a name="resources"></a>リソース

Machine learning のスクリプトを実行するためのユーザー アカウントをプロビジョニングする方法と、サービスの管理についての詳細については、次を参照してください。[構成 Advanced Analytics Extensions を管理および](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)です。

一般的なセキュリティ アーキテクチャの詳細についてを参照してください。

+ [R のセキュリティの概要](security-overview-sql-server-r.md)
+ [Python のセキュリティの概要](../python/security-overview-sql-server-python-services.md)
