---
title: SQL Server Machine Learning Services の高度な構成 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8384773f6db4c0ced2fc68e52cd78100c98c52fd
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396102"
---
# <a name="advanced-configuration-options-for-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services の高度な構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、セットアップ後は、外部スクリプトのランタイムと SQL Server での machine learning に関連するその他のサービスの構成を変更することの変更について説明します。

**適用対象:** SQL Server 2016 R Services、SQL Server 2017 の Machine Learning サービス

##  <a name="bkmk_Provisioning"></a> その他のユーザーのプロビジョニングが「学習マシン アカウントします。

外部スクリプトの処理で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]特権の低いローカル ユーザー アカウントのコンテキストで実行します。 個々 の低特権アカウントでこれらのプロセスを実行すると、次の利点があります。

+ 上の外部スクリプトのランタイム プロセスの特権の削減、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター
+ R や Python などの外部の実行時のセッション間での分離を提供します。

新しい Windows のセットアップの一部として*ユーザー アカウント プール*が作成される R や Python などの外部のランタイム プロセスを実行するために必要なローカル ユーザー アカウントを格納しています。 機械学習タスクをサポートするために必要に応じて、ユーザーの数を変更できます。 

さらに、データベース管理者は、機械学習が有効になっている任意のインスタンスに接続するには、このグループ権限を与える必要があります。 詳細については、次を参照してください。 [SQL Server Machine Learning Services のユーザー アカウント プールを変更](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)します。

上の protext の機密リソースに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、このグループのアクセス制御リスト (ACL) を定義することができます。 グループへのアクセスが拒否されたリソースを指定すると、R または Python のランタイムなどの外部プロセスによってアクセスを禁止することができます。

+ ユーザー アカウント プールは、特定のインスタンスにリンクされます。 ラーニングの有効にするコンピューターのインスタンスごとに、独立したプールのワーカー アカウントが必要です。 インスタンス間でアカウントを共有することはできません。

+ プールのユーザー アカウント名は、SQLInstanceName*nn*の形式になります。 たとえば、機械学習を既定のインスタンスを使用しているユーザー アカウント プールは MSSQLSERVER01、MSSQLSERVER02 といったアカウント名をサポートします。

+ ユーザー アカウント プールのサイズは静的であり、既定値は 20 です。 同時に起動できる外部のランタイム セッションの数は、このユーザー アカウント プールのサイズによって制限されます。 この制限を変更するには、管理者は、SQL Server 構成マネージャーを使用する必要があります。

ユーザー アカウント プールを変更する方法の詳細については、次を参照してください。 [SQL Server Machine Learning Services のユーザー アカウント プールを変更](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)します。

##  <a name="bkmk_ManagingMemory"></a> 外部スクリプト プロセスによって使用されるメモリを管理します。

既定では、machine learning の外部スクリプトのランタイムは、合計マシン メモリの 20% 以下に制限されます。 システムに依存は、一般に、この制限のモデルのトレーニングや多数のデータ行に基づく予測などの深刻な機械学習のタスクが不足します。 

機械学習をサポートするために、管理者は、この制限を増やすことができます。 これを行うときに予約されるメモリ量を削減する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]またはその他のサービスです。 外部リソース プールまたはプールを定義するリソース ガバナーを使用して R または Python のジョブを特定のリソース プールを割り当てることができますをも考慮する必要があります。

詳細については、次を参照してください。[機械学習用リソース ガバナンス](../../advanced-analytics/r/resource-governance-for-r-services.md)します。


## <a name="bkmk_Launchpad"></a>スタート パッド サービス アカウントを変更します。

個別の[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]machine learning サービスを構成した各インスタンスのサービスが作成されます。

既定では、スタート パッドは NT Service\MSSQLLaunchpad のアカウントを使用して実行するように構成され、このアカウントには、R スクリプトの実行に必要なすべてのアクセス許可がプロビジョニングされています。 ただし、このアカウントを変更する場合、スタート パッドできないことがありますを開始するか、外部スクリプトの実行される SQL Server インスタンスにアクセスします。

サービス アカウントを変更する場合は、**ローカル セキュリティ ポリシー** アプリケーションを使用し、各サービス アカウントのアクセス許可を更新して以下のアクセス許可を追加します。

+ プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
+ スキャン チェックを行わない (SeChangeNotifyPrivilege)
+ サービスとしてログオン (SeServiceLogonRight)
+ プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

SQL Server サービスの実行に必要なアクセス許可の詳細については、「[Configure Windows Service Accounts and Permissions (Windows サービス アカウントとアクセス許可の構成)](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」をご覧ください。

##  <a name="bkmk_ChangingConfig"></a> サービスの高度なオプションを変更します。

以前のバージョンの SQL Server 2016 R Services では、編集して、サービスの一部のプロパティを変更する可能性があります、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]構成ファイル。 

ただし、このファイルは構成を変更するため使用できなくします。 サービス アカウントとユーザーの数などのサービス構成に変更を反映する SQL Server 構成マネージャーを使用することをお勧めします。

**スタート パッドの構成を変更するには**

1. [[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)] を開きます。 
2. SQL Server スタート パッドを右クリックして**プロパティ**します。

    + サービス アカウントを変更するには、クリックして、**ログオン**タブ。

    + ユーザーの数を増やすをクリックして、**詳細**タブ。


**デバッグ設定を変更するには**

いくつかのプロパティは、デバッグなどの限られた状況で便利な可能性のある、スタート パッドの構成ファイルを使用してのみ変更できます。 構成ファイルの作成中に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップし、既定では、次の場所にプレーン テキスト ファイルとして保存されます。 `<instance path>\binn\rlauncher.config`

このファイルを変更するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの管理者になる必要があります。 ファイルを編集する場合は、変更を保存する前に、バックアップ コピーを作成することをお勧めします。

次の表は、高度な設定を示しています。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、許容される値を使用します。 

|**設定名**|**型**|**[説明]**|
|----|----|----|
|ジョブ\_クリーンアップ\_ON\_終了|Integer |これは内部でのみ設定 – この値は変更しないでください。 </br></br>セッションの完了後に外部のランタイム セッションごとに作成された一時作業フォルダーをクリーンアップするようにするかどうかを指定します。 この設定はデバッグに便利です。 </br></br>サポートされる値は**0** (無効) または**1** (有効)。 </br></br>既定値は 1 で、意味のログ ファイルは、終了時に削除されます。|
|トレース\_レベル|Integer |デバッグの目的で、MSSQLLAUNCHPAD のトレースの詳細レベルを構成します。 これも LOG_DIRECTORY 設定で指定されたパス内のトレース ファイルに影響します。 </br></br>サポートされている値: **1** (エラー)、 **2** (パフォーマンス) **3** (警告)、 **4** (情報)。 </br></br>既定値は 1、出力の警告のみを意味します。|

すべての設定が、キーと値のペアの形をとり、各設定は個別の行に表示されます。 たとえば、トレース レベルを変更するには行を追加する`Default: TRACE_LEVEL=4`します。

## <a name="see-also"></a>参照

[セキュリティに関する考慮事項](security-considerations-for-the-r-runtime-in-sql-server.md)
