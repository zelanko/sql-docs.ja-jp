---
title: Windows の分離の変更
description: この記事では、Windows 上の SQL Server 2019 の Machine Learning Services での分離メカニズムに対する変更について説明します。 これらの変更は、SQLRUserGroup、ファイアウォール規則、ファイルのアクセス許可、および暗黙の認証に影響します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4fae460e78682263c604d8e1e86ca40b7b62df97
ms.sourcegitcommit: 187f6d327421e64f1802a3085f88bbdb0c79b707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69531043"
---
# <a name="sql-server-2019-on-windows-isolation-changes-for-machine-learning-services"></a>Windows の SQL Server 2019:Machine Learning Services の分離の変更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、Windows 上の SQL Server 2019 の Machine Learning Services での分離メカニズムに対する変更について説明します。 これらの変更は、 **SQLRUserGroup**、ファイアウォール規則、ファイルのアクセス許可、および暗黙の認証に影響します。

詳細については、「 [Windows で SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md)をインストールする方法」を参照してください。

## <a name="changes-to-isolation-mechanism"></a>分離メカニズムの変更

Windows では、SQL Server 2019 セットアップにより、外部プロセスの分離メカニズムが変更されます。 この変更により、ローカルワーカーアカウントは、Windows で実行されているクライアントアプリケーションの分離テクノロジである[Appcontainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation)に置き換えられます。 

変更の結果、管理者には特定のアクション項目がありません。 新規またはアップグレードされたサーバーでは、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)から実行されるすべての外部スクリプトとコードが、自動的に新しい分離モデルに従います。 

要約すると、このリリースの主な違いは次のとおりです。

+ **SQL 制限ユーザーグループ (SQLRUserGroup)** の下にあるローカルユーザーアカウントは、外部プロセスを実行するために作成または使用されなくなりました。 AppContainers によって置き換えられます。
+ **SQLRUserGroup**のメンバーシップが変更されました。 メンバーシップは、複数のローカルユーザーアカウントの代わりに、SQL Server Launchpad サービスアカウントだけで構成されます。 R と Python のプロセスは、AppContainers を通じて分離されたスタートパッドサービス id で実行されるようになりました。

分離モデルは変更されていますが、SQL Server 2019 ではインストールウィザードとコマンドラインパラメーターは同じままです。 のインストールについては、「 [Install SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md)」を参照してください。

## <a name="about-appcontainer-isolation"></a>AppContainer の分離について

以前のリリースでは、 **SQLRUserGroup**には、外部プロセスの分離と実行に使用されるローカル Windows ユーザーアカウント (MSSQLSERVER00-MSSQLSERVER20) のプールが含まれていました。 外部プロセスが必要な場合、SQL Server Launchpad サービスは使用可能なアカウントを取得し、それを使用してプロセスを実行します。 

SQL Server 2019 では、セットアップでローカルワーカーアカウントが作成されなくなりました。 代わりに、 [Appcontainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation)によって分離が実現されます。 実行時に、ストアドプロシージャまたはクエリで埋め込みスクリプトやコードが検出されると、SQL Server は、拡張機能固有の起動ツールの要求を使用してスタートパッドを呼び出します。 スタートパッドは、id の下にあるプロセスで適切なランタイム環境を呼び出し、それを含むように AppContainer をインスタンス化します。 この変更は、ローカルアカウントとパスワードの管理が不要になったため、有益です。 また、ローカルユーザーアカウントが禁止されているインストールでは、ローカルユーザーアカウントの依存関係を削除することで、この機能を使用できるようになります。

SQL Server によって実装された AppContainers は内部メカニズムです。 プロセスモニターに AppContainers の物理的な証拠が表示されることはありませんが、プロセスがネットワーク呼び出しを行わないように、セットアップによって作成された送信ファイアウォールルールで見つけることができます。

## <a name="firewall-rules-created-by-setup"></a>セットアップによって作成されたファイアウォール規則

既定では、SQL Server は、ファイアウォール規則を作成することによって送信接続を無効にします。 以前は、これらの規則はローカルユーザーアカウントに基づいていました。セットアップでは、メンバーへのネットワークアクセスを拒否する**SQLRUserGroup**の送信規則が1つ作成されました (各ワーカーアカウントは rule_ のサブジェクトとしてローカルプリンシパルとして一覧表示されていました。 

AppContainers への移行の一環として、AppContainer Sid に基づく新しいファイアウォールルールがあります。これは SQL Server セットアップによって作成された20の AppContainers それぞれに1つです。 ファイアウォール規則名の名前付け規則は、 **SQL Server インスタンス MSSQLSERVER の appcontainer-00 のネットワークアクセスをブロック**します。ここで、00は appcontainer の番号 (既定では 00-20)、MSSQLSERVER は SQL Server インスタンスの名前です。 

> [!Note]
> ネットワーク呼び出しが必要な場合は、Windows ファイアウォールで送信ルールを無効にすることができます。

## <a name="program-file-permissions"></a>プログラムファイルのアクセス許可

以前のリリースと同様に、 **SQLRUserGroup**は、 **Binn**、 **R_SERVICES**、 **PYTHON_SERVICES**の各ディレクトリ SQL Server 内の実行可能ファイルに対する読み取りおよび実行のアクセス許可を引き続き提供します。 このリリースでは、 **SQLRUserGroup**の唯一のメンバーは SQL Server Launchpad サービスアカウントです。  スタートパッドサービスが R または Python の実行環境を開始すると、プロセスはスタートパッドサービスとして実行されます。

## <a name="implied-authentication"></a>暗黙の認証

以前と同様に、スクリプトまたはコードでは、信頼された認証を使用して SQL Server に接続してデータまたはリソースを取得する必要がある場合に、*暗黙的な認証*に対して追加の構成が必要になります。 追加の構成では、 **SQLRUserGroup**のデータベースログインを作成する必要があります。この場合、その唯一のメンバーは、複数のワーカーアカウントではなく、1つの SQL Server Launchpad サービスアカウントになります。 このタスクの詳細については、「[データベースユーザーとしての SQLRUserGroup の追加](../security/create-a-login-for-sqlrusergroup.md)」を参照してください。


## <a name="symbolic-link-created-by-setup"></a>セットアップによって作成されたシンボリックリンク

SQL Server セットアップの一部として、現在の既定の**R_SERVICES**と**PYTHON_SERVICES**にシンボリックリンクが作成されます。 このリンクを作成しない場合は、"すべてのアプリケーションパッケージ" の読み取りアクセス許可をフォルダーまでの階層に付与することをお勧めします。


## <a name="see-also"></a>関連項目

+ [Windows に SQL Server Machine Learning Services をインストールする](sql-machine-learning-services-windows-install.md)
+ [Linux に SQL Server Machine Learning Services をインストールする](../../linux/sql-server-linux-setup-machine-learning.md)
