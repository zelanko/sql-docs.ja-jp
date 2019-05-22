---
title: SQL Server 2019 - SQL Server Machine Learning サービスの違い
description: R と Python の SQL Server machine learning 拡張機能の SQL Server 2019 のプレビュー リリースでは新機能について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3d549bdc96e09ed0b9b0235ada51274201f1b91a
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994230"
---
# <a name="differences-in-sql-server-machine-learning-services-installation-in-sql-server-2019"></a>SQL Server 2019 で SQL Server Machine Learning Services のインストールの違い  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

、Windows では、SQL Server 2019 セットアップは、外部プロセス用の分離メカニズムを変更します。 この変更でローカルのワーカー アカウントが置き換えられます[AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation)Windows で実行されているクライアント アプリケーションの分離テクノロジ。 

変更の結果として、管理者の特定のアクション アイテムはありません。 新規またはアップグレードされたサーバーでは、すべての外部スクリプトおよびから実行されるコード[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)自動的に新しい分離モデルに従います。 

このリリースでの主な相違点は、集計。

+ ローカル ユーザー アカウント。 対象**SQL 制限されたユーザー グループ (SQLRUserGroup)** が不要になった作成または外部プロセスを実行するために使用します。 AppContainers を交換します。
+ **SQLRUserGroup**メンバーシップが変更されました。 複数のローカル ユーザー アカウントではなく、メンバーシップは、SQL Server スタート パッド サービス アカウントだけで構成されます。 R と Python のプロセスは、今すぐスタート パッド サービス id、AppContainers を通じて分離で実行されます。

分離モデルが変更されていますが、インストール ウィザードとコマンド ライン パラメータが SQL Server 2019 で同じになります。 インストールについては、次を参照してください。 [SQL Server Machine Learning のサービスをインストール](sql-machine-learning-services-windows-install.md)します。

## <a name="about-appcontainer-isolation"></a>AppContainer 分離について

以前のリリースで**SQLRUserGroup**ローカル Windows ユーザー アカウント (MSSQLSERVER00 MSSQLSERVER20) を分離し、外部プロセスを実行するためのプールに含まれています。 外部プロセスが必要なときに SQL Server スタート パッド サービスが使用可能なアカウントを取得して、プロセスを実行します。 

SQL Server 2019、セットアップは不要になったローカル ワーカー アカウントを作成します。 によって分離を実現する代わりに、 [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation)します。 埋め込まれたスクリプトまたはコードが検出された場合、ストアド プロシージャまたはクエリで、実行時に、SQL Server は、要求で拡張機能に固有の起動ツールのスタート パッドを呼び出します。 スタート パッドは、その id でのプロセスで適切なランタイム環境を呼び出し、そのを含む、AppContainer をインスタンス化します。 ローカル アカウントとパスワードの管理が必要になるために、この変更の使用をお勧めします。 また、ローカル ユーザー アカウントは禁止されている、インストールでローカル ユーザー アカウントの依存関係をなくすこと、この機能を使用するようになりました。

、SQL Server で実装された AppContainers は、内部のメカニズムです。 プロセス モニターで AppContainers の物理的な証拠が表示されなくなります、中には、プロセスがネットワーク呼び出しを行うことを防ぐためにセットアップによって作成された送信ファイアウォール規則で見つけることができます。

## <a name="firewall-rules-created-by-setup"></a>セットアップによって作成されたファイアウォール規則

既定では、SQL Server には、ファイアウォール ルールを作成して送信接続が無効にします。 以前は、これらの規則は、セットアップでの 1 つの送信規則を作成する場所のローカル ユーザー アカウントに基づくされた**SQLRUserGroup**そのメンバーへのネットワーク アクセスを拒否する (各ワーカー アカウントはローカルの原則、rule_ の対象として表示されました。 

AppContainer Sid に基づいて、新しいファイアウォール規則がある AppContainers への移行の一環として、: SQL Server セットアップによって作成された 20 AppContainers ごとに 1 つ。 ファイアウォール規則の名前の名前付け規則は**AppContainer 00 の SQL Server インスタンス MSSQLSERVER でネットワーク アクセスをブロック**00 (00-20 既定)、AppContainer の数には、MSSQLSERVER が、SQL の名前サーバー インスタンスです。 

> [!Note]
> ネットワーク呼び出しが必要な場合は、Windows ファイアウォールの送信の規則を無効にできます。

## <a name="program-file-permissions"></a>プログラム ファイルのアクセス許可

以前のリリースと同様、 **SQLRUserGroup**読み取りを行い、実行可能ファイルの SQL Server を実行する権限は引き続き**Binn**、 **R_SERVICES**、および**PYTHON_SERVICES**ディレクトリ。 このリリースでは、唯一のメンバーで**SQLRUserGroup**は、SQL Server スタート パッド サービス アカウントです。  スタート パッド サービスには、R または Python の実行環境が起動するときに、スタート パッド サービスとして、プロセスが実行されます。

## <a name="implied-authentication"></a>暗黙の認証

前に、追加の構成は引き続き必要ですが、*暗黙の認証*内にスクリプトまたはコードが信頼済みの認証を使用して、データやリソースを取得する SQL Server に接続する場合。 追加の構成では、データベース ログインを作成する必要があります**SQLRUserGroup**、その唯一のメンバーは、複数のワーカー アカウントではなく、1 つの SQL Server スタート パッド サービス アカウントではようになりました。 このタスクの詳細については、次を参照してください。[データベース ユーザーとしての SQLRUserGroup の追加](../security/add-sqlrusergroup-to-database.md)します。


## <a name="symbolic-link-created-by-setup"></a>セットアップによって作成されたシンボリック リンク

現在の既定値にシンボリック リンクが作成された**R_SERVICES**と**PYTHON_SERVICES** SQL Server セットアップの一部として。 このリンクを作成しない場合は、代替策は、フォルダーに至るまで、階層に 'all application packages' の読み取りアクセス許可を付与します。


## <a name="see-also"></a>関連項目

+ [SQL Server Machine Learning では、Windows サービスをインストールします。](sql-machine-learning-services-windows-install.md)

+ [Linux 上の SQL Server 2019 Machine Learning Services をインストールします。](../../linux/sql-server-linux-setup-machine-learning.md)
