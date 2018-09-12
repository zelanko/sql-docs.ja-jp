---
title: SQL Server スタート パッド サービス アカウントの構成 |Microsoft Docs
description: SQL Server での外部スクリプト実行に使用する SQL Server スタート パッド サービス アカウントを変更する方法。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0afdb02c578de92bc91c5f47e973148136ebd919
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892877"
---
# <a name="sql-server-launchpad-service-configuration"></a>SQL Server スタート パッド サービスの構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

個別の[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]データベース エンジンのインスタンスが SQL Server machine learning (R または Python) 統合を追加したサービスが作成されます。

## <a name="service-account-configuration"></a>サービス アカウントの構成

実行するように既定では、SQL Server スタート パッドが構成されている**NT service \mssqllaunchpad**、外部スクリプトを実行するすべての必要なアクセス許可でがプロビジョニングされます。 このアカウントからのアクセス許可を削除すると、または外部スクリプトの実行される SQL Server インスタンスへのアクセスに失敗を開始するスタート パッドがあります。

このアカウントに必要なアクセス許可は、以下に示します。 サービス アカウントを変更する場合に使用することを確認して、**ローカル セキュリティ ポリシー**アプリケーションにこれらのアクセス許可を含めます。

+ プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
+ スキャン チェックを行わない (SeChangeNotifyPrivilege)
+ サービスとしてログオン (SeServiceLogonRight)
+ プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

SQL Server サービスの実行に必要なアクセス許可の詳細については、「[Configure Windows Service Accounts and Permissions (Windows サービス アカウントとアクセス許可の構成)](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」をご覧ください。

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>構成プロパティ

1. [[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)] を開きます。 

2. SQL Server スタート パッドを右クリックして**プロパティ**します。

    + サービス アカウントを変更するには、クリックして、**ログオン**タブ。

    + ユーザーの数を増やすをクリックして、**詳細**タブ。

> [!Note]
> 以前のバージョンの SQL Server 2016 R Services では、編集して、サービスの一部のプロパティを変更する可能性があります、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]構成ファイル。 このファイルは構成を変更するのには使用されません。 SQL Server 構成マネージャーは、サービス アカウントとユーザーの数などのサービス構成の変更を適切なアプローチです。

#### <a name="debug-settings"></a>デバッグの設定

いくつかのプロパティは、デバッグなどの限られた状況で便利な可能性のある、スタート パッドの構成ファイルを使用してのみ変更できます。 構成ファイルの作成中に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップし、既定では、次の場所にプレーン テキスト ファイルとして保存されます。 `<instance path>\binn\rlauncher.config`

このファイルを変更するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの管理者になる必要があります。 ファイルを編集する場合は、変更を保存する前に、バックアップ コピーを作成することをお勧めします。

次の表は、高度な設定を示しています。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、許容される値を使用します。 

|**設定名**|**型**|**[説明]**|
|----|----|----|
|ジョブ\_クリーンアップ\_ON\_終了|Integer |これは内部でのみ設定 – この値は変更しないでください。 </br></br>セッションの完了後に外部のランタイム セッションごとに作成された一時作業フォルダーをクリーンアップするようにするかどうかを指定します。 この設定はデバッグに便利です。 </br></br>サポートされる値は**0** (無効) または**1** (有効)。 </br></br>既定値は 1 で、意味のログ ファイルは、終了時に削除されます。|
|トレース\_レベル|Integer |デバッグの目的で、MSSQLLAUNCHPAD のトレースの詳細レベルを構成します。 これも LOG_DIRECTORY 設定で指定されたパス内のトレース ファイルに影響します。 </br></br>サポートされている値: **1** (エラー)、 **2** (パフォーマンス) **3** (警告)、 **4** (情報)。 </br></br>既定値は 1、出力の警告のみを意味します。|

すべての設定が、キーと値のペアの形をとり、各設定は個別の行に表示されます。 たとえば、トレース レベルを変更するには行を追加する`Default: TRACE_LEVEL=4`します。

## <a name="see-also"></a>関連項目

[機能拡張フレームワーク](../concepts/extensibility-framework.md)
