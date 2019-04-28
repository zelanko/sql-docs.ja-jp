---
title: 外部スクリプト - SQL Server Machine Learning Services のスケールの同時実行
description: SQL Server Machine Learning サービスをスケールするユーザー アカウント プールや同時実行の並列 R と Python スクリプトの実行を構成します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 9f32e51122df8d2d13d6eada726a1a5e9bea82f0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659513"
---
# <a name="scale-concurrent-execution-of-external-scripts-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services での外部スクリプトの同時実行のスケール
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスによるタスクの実行をサポートするために、[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] のインストール プロセスの一部として、新しい Windows *"ユーザー アカウント プール"* が作成されました。 これらのワーカー アカウントの目的は、異なる SQL ユーザーによる外部スクリプトの同時実行を分離します。

この記事では、既定の構成と容量をワーカー アカウントと SQL Server Machine Learning Services の外部スクリプトの同時実行の数をスケール調整する既定の構成を変更する方法について説明します。

## <a name="worker-account-group"></a>ワーカー アカウント グループ

によって Windows アカウント グループが作成された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]learning をインストールして有効にするコンピューターは、各インスタンスをセットアップします。

- 既定のインスタンスでは、グループ名は **SQLRUserGroup** です。 名前は、R または Python を使用するかどうかは同じです。
- 名前付きインスタンスでは、既定のグループ名にインスタンス名が付加されます: たとえば、 **SQLRUserGroupMyInstanceName**。

既定では、ユーザー アカウント プールには 20 個のユーザー アカウントが含まれています。 ほとんどの場合に、20 は、machine learning タスクをサポートするために十分ながアカウントの数を変更することができます。 アカウントの最大数は、100 です。

- 既定のインスタンスでは、個々のアカウントは **MSSQLSERVER01** ～ **MSSQLSERVER20** と命名されます。
- 名前付きインスタンスの場合、個々のアカウントはインスタンス名に基づいて命名されます。たとえば、 **MyInstanceName01** ～ **MyInstanceName20**。

1 つ以上のインスタンスは、machine learning を使用している場合、コンピューターが複数のユーザー グループになります。 グループは、インスタンス間で共有できません。

> [!Note]
> SQL Server の 2019 で**SQLRUserGroup**は 1 つのメンバーが複数のワーカー アカウントではなく、1 つの SQL Server スタート パッド サービス アカウントになっています。

<a name = "HowToChangeGroup"> </a>

## <a name="number-of-worker-accounts"></a>ワーカー アカウントの数

アカウント プール内のユーザー数を変更するには、以下に示すように、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスのプロパティを編集する必要があります。

各ユーザー アカウントに関連付けられるパスワードはランダムに生成されますが、アカウントの作成後に変更することもできます。

1. SQL Server 構成マネージャーを開き、**[SQL Server のサービス]** をクリックします。
2. SQL Server スタート パッド サービスをダブルクリックし、サービスが実行されている場合は、サービスを停止します。
3.  **[サービス]** タブで、[開始モード] が [自動] に設定されていることを確認します。 スタート パッドが実行されていない場合、外部スクリプトを開始できません。
4.  **[詳細設定]** タブをクリックし、必要であれば、**[外部ユーザーの数]** の値を編集します。 この設定を制御異なる SQL ユーザーの数できます外部スクリプト実行セッションを同時にします。 既定では 20 個のアカウントです。 ユーザーの最大数は、100 です。
5. パスワードを定期的に変更するポリシーが組織で実施されている場合は、オプションで、**[外部ユーザーのパスワードのリセット]** を _[はい]_ に設定できます。 これを行うと、ユーザー アカウントに対してスタート パッドが保持している暗号化パスワードが再生成されます。 詳しくは、「[パスワード ポリシーの実施](../security/sql-server-launchpad-service-account.md#bkmk_EnforcePolicy)」をご覧ください。
6.  スタート パッド サービスを再起動します。

## <a name="managing-workloads"></a>ワークロードの管理

外部スクリプト セッションの数、アクティブな同時に、このプール内のアカウントの数を決定します。  既定では、20 個のアカウントが作成になり、20 人のユーザーがアクティブの R または Python セッション一度に 1 つを持つことを意味します。 20 を超える同時実行スクリプトを実行する場合は、ワーカー アカウントの数を増やすことができます。

同じユーザーが同時に複数の外部スクリプトを実行すると、セッションがそのユーザーが実行すべて同じワーカー アカウントを使用します。 たとえば、1 人のユーザーには、リソースが許すが、すべてのスクリプトは、1 つのワーカー アカウントを使用して実行がいれば、同時に実行される 100 のさまざまな R スクリプトがあります。

次のようにサポートできますが、ワーカー アカウントの数と 1 人のユーザーが実行できる同時セッション数は、サーバーのリソースによってのみ制限されます。 通常、R ランタイムの使用時に遭遇する最初のボトルネックは、メモリです。

Python または R スクリプトで使用できるリソースは、SQL Server によって管理されます。 SQL Server の DMV を使用してリソースの使用状況を監視するか、または関連する Windows ジョブ オブジェクトのパフォーマンス カウンターを見て、サーバー メモリの使用量を必要に応じて調整することをお勧めします。 SQL Server Enterprise Edition がある場合は、構成することで、外部スクリプトを実行するために使用されるリソースを割り当てることができます、[外部リソース プール](how-to-create-a-resource-pool.md)します。

## <a name="see-also"></a>参照

容量を構成する方法の詳細については、次の記事を参照してください。

- [R Services の SQL Server の構成](../../advanced-analytics/r/sql-server-configuration-r-services.md)
- [R Services のパフォーマンスのケース スタディ](../../advanced-analytics/r/performance-case-study-r-services.md)