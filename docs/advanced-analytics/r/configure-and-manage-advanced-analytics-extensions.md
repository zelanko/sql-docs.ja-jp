---
title: "Machine Learning のサービスの構成オプションの詳細 |Microsoft ドキュメント"
ms.custom: SQL2016_New_Updated
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: "21"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 24f2082572cdb314257826570471548f87b1b60e
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="advanced-configuration-options-for-machine-learning-services"></a>Machine Learning のサービスの高度な構成オプション

この記事では、外部スクリプトの実行時と SQL Server での機械学習に関連付けられているその他のサービスの構成を変更するのセットアップ後に実行できる変更について説明します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

##  <a name="bkmk_Provisioning"></a>その他のユーザーのプロビジョニング アカウントのマシンの学習

外部スクリプトのプロセスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]特権の低いローカル ユーザー アカウントのコンテキストで実行します。 個々 の低特権アカウントでこれらのプロセスを実行すると、次の利点があります。

+ 外部スクリプトのランタイム プロセスの特権を減らすことが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター
+ R、Python などの外部のランタイム セッション間が分離を提供します。

新しい Windows のセットアップの一部として*ユーザー アカウント プール*が作成される R、Python などの外部のランタイム プロセスを実行するために必要なローカル ユーザー アカウントを格納しています。 機械学習タスクをサポートするために必要に応じて、ユーザーの数を変更することができます。 

さらに、データベース管理者は、機械学習が有効になっている任意のインスタンスに接続するには、このグループ権限を与える必要があります。 詳細については、次を参照してください。 [SQL Server の Machine Learning のサービスのユーザー アカウント プールを変更する](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

Protext 機密性の高いリソースに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、このグループのアクセス制御リスト (ACL) を定義することができます。 グループへのアクセスを拒否されているリソースを指定すると、R、または Python ランタイムなどの外部プロセスによってアクセスを禁止することができます。

+ ユーザー アカウント プールは、特定のインスタンスにリンクされます。 学習の有効などのコンピューターでインスタンスごとに、独立したプールのワーカー アカウントが必要です。 インスタンス間でアカウントを共有することはできません。

+ プールのユーザー アカウント名は、SQLInstanceName*nn*に関連するその他のサービスの構成に軽微な変更を行うことができます。 たとえば、機械学習で既定のインスタンスを使用している場合、ユーザー アカウント プールは MSSQLSERVER01、MSSQLSERVER02 といったアカウント名をサポートします。

+ ユーザー アカウント プールのサイズは静的であり、既定値は 20 です。 同時に起動できる外部のランタイム セッションの数は、このユーザー アカウント プールのサイズによって制限されます。 この制限を変更するには、管理者は、SQL Server 構成マネージャーを使用する必要があります。

ユーザー アカウント プールを変更する方法の詳細については、次を参照してください。 [SQL Server の Machine Learning のサービスのユーザー アカウント プールを変更する](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

##  <a name="bkmk_ManagingMemory"></a>外部スクリプトのプロセスによって使用されるメモリを管理します。

既定では、機械学習の外部スクリプトのランタイムは、合計マシン メモリの 20% 以下に制限されます。 システムに依存している場合が一般に、ありますこの制限のモデルのトレーニングまたは多くのデータ行の予測などの深刻な機械学習タスクが不十分であります。 

機械学習をサポートするために、管理者は、この制限を増やすことができます。 これを行うときに予約されるメモリの量を削減する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]またはその他のサービスです。 R または Python のジョブを特定のリソース プールを割り当てることができるように、リソース ガバナーを使用して外部リソース プールまたはプールを定義するも考慮する必要があります。

詳細については、次を参照してください。[機械学習用リソース ガバナンス](../../advanced-analytics/r/resource-governance-for-r-services.md)です。


## <a name="bkmk_Launchpad"></a>スタート パッド サービス アカウントを変更します。

個別の[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]機械学習サービスを構成した各インスタンスのサービスが作成されます。

既定では、スタート パッドは NT Service\MSSQLLaunchpad のアカウントを使用して実行するように構成され、このアカウントには、R スクリプトの実行に必要なすべてのアクセス許可がプロビジョニングされています。 ただし、このアカウントを変更する場合、スタート パッドできないことがありますを起動したり、外部スクリプトを実行可能な SQL Server インスタンスにアクセスします。

サービス アカウントを変更する場合は、**ローカル セキュリティ ポリシー** アプリケーションを使用し、各サービス アカウントのアクセス許可を更新して以下のアクセス許可を追加します。

+ プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
+ スキャン チェックを行わない (SeChangeNotifyPrivilege)
+ サービスとしてログオン (SeServiceLogonRight)
+ プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

SQL Server サービスの実行に必要なアクセス許可の詳細については、「[Configure Windows Service Accounts and Permissions (Windows サービス アカウントとアクセス許可の構成)](https://msdn.microsoft.com/library/ms143504.aspx#Windows)」をご覧ください。

##  <a name="bkmk_ChangingConfig"></a>サービスの高度なオプションを変更します。

以前のバージョンの SQL Server 2016 の R Services では、編集して、サービスの一部のプロパティを変更する可能性があります、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]構成ファイル。 

ただし、このファイルは、不要になった構成の変更を使用します。 サービス アカウントとユーザーの数などのサービス構成に変更を反映する SQL Server 構成マネージャーを使用することをお勧めします。

**スタート パッドの構成を変更するには**

1. [[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)] を開きます。 
2. SQL Server スタート パッドを右クリックし **プロパティ**です。

    + サービス アカウントを変更する をクリックして、**ログオン**タブです。

    + ユーザーの数を増やすをクリックして、**詳細** タブ。


**デバッグ設定を変更するには**

いくつかのプロパティは、デバッグなど、限られた状況で役に立ちます可能性のある、スタート パッドの構成ファイルを使用してのみ変更できます。 中に、構成ファイルが作成された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップし、既定では、次の場所にプレーン テキスト ファイルとして保存します。`<instance path>\binn\rlauncher.config`

このファイルを変更するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの管理者になる必要があります。 ファイルを編集する場合は、変更を保存する前に、バックアップ コピーを作成することをお勧めします。

次の表に、高度な設定[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、許容される値を使用します。 

|**設定名**|**型**|**Description**|
|----|----|----|
|ジョブ\_クリーンアップ\_ON\_終了|Integer |これは内部でのみ設定 – この値は変更しないでください。 </br></br>セッションが完了した後はかどうか外部のランタイム セッションごとに作成された一時作業フォルダーをクリーンアップにする必要がありますを指定します。 この設定はデバッグに便利です。 </br></br>サポートされる値は**0** (無効) または**1** (有効) です。 </br></br>既定値は 1、意味のログ ファイルは、終了時に削除されます。|
|トレース\_レベル|Integer |デバッグの目的で、MSSQLLAUNCHPAD のトレースの詳細レベルを構成します。 これにより、LOG_DIRECTORY 設定で指定されたパス内のトレース ファイルが影響します。 </br></br>サポートされる値: **1** (エラー)、 **2** (パフォーマンス)、 **3** (警告)、 **4** (情報)。 </br></br>既定値は 1、出力警告のみを意味します。|

すべての設定が、キーと値のペアの形をとり、各設定は個別の行に表示されます。 たとえば、トレース レベルを変更するには行を追加する`Default: TRACE_LEVEL=4`です。

## <a name="see-also"></a>参照

[セキュリティに関する考慮事項](security-considerations-for-the-r-runtime-in-sql-server.md)
