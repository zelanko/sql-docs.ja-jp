---
title: SQL Server スタート パッド サービス アカウントの構成 |Microsoft Docs
description: SQL Server での外部スクリプト実行に使用する SQL Server スタート パッド サービス アカウントを変更する方法。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 8af27f3bc9fb3e5b602ef6ad5555d9bd8c6720ca
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419117"
---
# <a name="sql-server-launchpad-service-configuration"></a>SQL Server スタート パッド サービスの構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]は管理し、フルテキスト インデックス作成とクエリ サービスが、フルテキスト クエリを処理するための別のホストを起動するのと同様に、外部のスクリプトを実行するサービスです。

詳細については、スタート パッドのセクションを参照してください[SQL Server Machine Learning Services で拡張可能アーキテクチャ](../../advanced-analytics/concepts/extensibility-framework.md#launchpad)と[は、SQL Server Machine Learning の機能拡張フレームワークのセキュリティの概要。サービス](../../advanced-analytics/concepts/security.md#launchpad)します。

## <a name="account-permissions"></a>アカウントのアクセス許可

実行するように既定では、SQL Server スタート パッドが構成されている**NT service \mssqllaunchpad**、外部スクリプトを実行するすべての必要なアクセス許可でがプロビジョニングされます。 このアカウントからのアクセス許可を削除すると、スタート パッドを開始するか、外部スクリプトの実行される SQL Server インスタンスへのアクセスに失敗している可能性があります。

サービス アカウントを変更する場合に使用することを確認して、[ローカル セキュリティ ポリシー コンソール](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/how-to-configure-security-policy-settings)します。

このアカウントに必要なアクセス許可は、次の表に表示されます。

| グループ ポリシー設定 | 定数の名前 |
|----------------------|---------------|
| [プロセスに対してメモリ クォータを調整します。](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/adjust-memory-quotas-for-a-process) | SeIncreaseQuotaPrivilege | 
| [走査チェックのバイパス](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/bypass-traverse-checking) | SeChangeNotifyPrivilege | 
| [サービスとしてログオンします。](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/log-on-as-a-service) | SeServiceLogonRight | 
| [プロセス レベル トークンを置き換える](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/replace-a-process-level-token) | SeAssignPrimaryTokenPrivilege | 

SQL Server サービスの実行に必要なアクセス許可の詳細については、「[Configure Windows Service Accounts and Permissions (Windows サービス アカウントとアクセス許可の構成)](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」をご覧ください。

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>構成プロパティ

通常、サービスの構成を変更する理由はありません。 外部プロセス (既定では 20)、またはパスワードの数のワーカー アカウント ポリシーのリセット、変更できるプロパティには、サービス アカウントが含まれます。

1. [[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)] を開きます。

2. SQL Server のサービス の下には、SQL Server スタート パッドを右クリックして**プロパティ**します。
  + サービス アカウントを変更するには、クリックして、**ログオン**タブ。
  + ユーザーの数を増やすをクリックして、**詳細**タブを変更、**セキュリティ コンテキストの数**します。

> [!Note]
> 以前のバージョンの SQL Server 2016 R Services では、編集して、サービスの一部のプロパティを変更する可能性があります、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]構成ファイル。 このファイルは構成を変更するのには使用されません。 SQL Server 構成マネージャーは、サービス アカウントとユーザーの数などのサービス構成の変更を適切なアプローチです。

## <a name="debug-settings"></a>デバッグの設定

いくつかのプロパティは、デバッグなどの限られた状況で便利な可能性のある、スタート パッドの構成ファイルを使用してのみ変更できます。 構成ファイルの作成中に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップし、既定でプレーン テキスト ファイルとして保存されます`<instance path>\binn\rlauncher.config`します。

このファイルを変更するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの管理者になる必要があります。 ファイルを編集する場合は、変更を保存する前に、バックアップ コピーを作成することをお勧めします。

次の表は、高度な設定を示しています。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、許容される値を使用します。

|**設定名**|**型**|**[説明]**|
|----|----|----|
|ジョブ\_クリーンアップ\_ON\_終了|Integer |これは内部でのみ設定 – この値は変更しないでください。 </br></br>セッションの完了後に外部のランタイム セッションごとに作成された一時作業フォルダーをクリーンアップするようにするかどうかを指定します。 この設定はデバッグに便利です。 </br></br>サポートされる値は**0** (無効) または**1** (有効)。 </br></br>既定値は 1 で、意味のログ ファイルは、終了時に削除されます。|
|トレース\_レベル|Integer |デバッグの目的で、MSSQLLAUNCHPAD のトレースの詳細レベルを構成します。 これも LOG_DIRECTORY 設定で指定されたパス内のトレース ファイルに影響します。 </br></br>サポートされている値: **1** (エラー)、 **2** (パフォーマンス) **3** (警告)、 **4** (情報)。 </br></br>既定値は 1、出力エラーのみを意味します。|

すべての設定が、キーと値のペアの形をとり、各設定は個別の行に表示されます。 たとえば、トレース レベルを変更するには行を追加する`Default: TRACE_LEVEL=4`します。

## <a name="enforcing-password-policy"></a>パスワード ポリシーの実施

パスワードを定期的に変更するポリシーが組織で実施されている場合は、ユーザー アカウントに対してスタート パッドが保持している暗号化パスワードを、強制的に再生成しなければならない場合があります。

この設定を有効にし、パスワードの更新を強制するには、SQL Server 構成マネージャーでスタート パッド サービスの **[プロパティ]** ペインを開き、**[詳細設定]** をクリックして、**[外部ユーザーのパスワードのリセット]** を **[はい]** に変更します。 この変更を適用すると、すべてのユーザー アカウントのパスワードが直ちに再生成されます。 この変更後、外部のスクリプトを実行するには、時点では、新しく生成されたパスワードを読み取ることは、スタート パッド サービスを再起動する必要があります。

パスワードを定期的にリセットするには、このフラグを手動で設定するか、スクリプトを使用します。

## <a name="next-steps"></a>次の手順

+ [機能拡張フレームワーク](../concepts/extensibility-framework.md)
+ [セキュリティの概要](../concepts/security.md)
