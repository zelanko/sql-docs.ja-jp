---
title: "Azure SQL データベースでの R の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e3c781449a8f7a1b236508cd21b8c00ff175774f
ms.openlocfilehash: 619921bbf00801fd5930a1c1b110e69a9fd05a81
ms.contentlocale: ja-jp
ms.lasthandoff: 09/30/2017

---
# <a name="using-r-in-azure-sql-database"></a>Azure SQL データベースでの R の使用

、2017 年 10 月の時点では、Azure SQL データベースは、R コードでのデータベースの SQL Server 2016 での R Services のような、ストアド プロシージャを使用して実行をサポートします。

この記事では、機能の概要について説明し、既知の制限について説明します。

> [!NOTE]
> このリリースでは、初期のプレビュー バージョンあり、テストと探索のみのものです。 実稼働バージョンは、2018年でいずれかの時点でリリースされます。 正確なリリース日とビルドは、ユーザーからのフィードバックに基づくされます。 そのため、機能を実行してください。 お知らせは、どの機能が重要にするをお勧めします。 
> 
> リリースのスケジュールについては、次を参照してください。、 [SQL Server ブログ](https://blogs.technet.microsoft.com/dataplatforminsider/)または[Microsoft R Server のブログ](https://blogs.msdn.microsoft.com/rserver/)です。

## <a name="features"></a>機能

プレビュー リリースには、次の機能が提供されます。

+ 機械学習ソリューションの配置が容易にストアド プロシージャを使用して R を呼び出す
+ モデルからスコアを使用して取得し、クラウド データベースに接続できる任意のアプリケーション
+ ネイティブの R ランタイムを使用しなくても高速スコアリングのための予測関数を使用してスコア付けをサポートしています

プレビュー バージョンに固有の制限事項を参照してください。[制限と既知の問題](#bkmk_restrictions)です。

### <a name="components"></a>コンポーネント

全体的なアーキテクチャは、SQL Server コンピューターの R Services に似ています。

**セキュリティ**

+ SQL Server の信頼されたスタート パッドは、R ジョブの実行を管理し、プロセスの有効期間を制御します。 

**R パッケージ**

+ プレビュー リリースでは、Microsoft R Open 3.3.3、および Microsoft R Server バージョン 9.2 です。 [RevoScaleR パッケージ](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)がプレインストールされています。

+ いくつかの R パッケージが削除されたか、Azure 環境での使用量を削減するように変更します。 たとえば、 **mrsdeploy**は Azure SQL データベースに含まれません。

**[パフォーマンス]**

+ トレーニング セットとデータがメモリに収まる場所の任意のモデルからスコアをサポートします。  使用可能なメモリの量は、データベースのエディションによって異なります。 
+ 使用して単純な並列処理をサポート、@parallelストリーミング R スクリプトの実行ができるだけでなく、1 つの引数を = 
+ プレビューでは、データベースごとに同時に実行され、1 つの R スクリプトに制限されます。

**言語**

将来のリリースのロードマップには、その他のパッケージおよび Python のサポートが含まれています。

## <a name="restrictions"></a>制限

このセクションには、プレビュー リリースに適用されるいくつかの追加制限が一覧表示します。

### <a name="upgrading-r-components-and-adding-packages-not-supported"></a>R コンポーネントをアップグレードして、サポートされていないパッケージを追加します。

Azure SQL データベースは、管理されたサービスと、お客様は、R コンポーネントをアップグレードを管理するのには必要ありません。 プレビュー リリースでは、利用可能なインストール パッケージを使用してください。

利用可能になる R およびその他の機械学習でコンポーネントへのアップグレードがリリースされます。

### <a name="availability"></a>可用性

R およびその他の機械学習で Azure SQL データベースのスクリプトを実行する権限は、西中央アメリカ地域のみのプレビュー機能です。 西ヨーロッパなどの他の領域に拡張は、今後のリリース予定です。

Azure SQL データベースで R を実行するには、十分な記憶域とメモリが必要です。 現在、次のデータベース サービス階層とパフォーマンス レベルがサポートされます。

+ Premium サービス階層: P1、P2、P4、P6、P11、P15 
+ Premium の RS サービス層: PRS1、PRS2、PRS4、PRS6 
+ Premium エラスティック プール: 125 Edtu 以上 
+ Premium RS 弾力性プール: 125 Edtu 以上 

### <a name="resource-management"></a>リソース管理

このリリースは、R のインストールをカスタマイズする機能や R スクリプトの使用状況を監視する機能をサポートしていません。

たとえば、R スクリプトの実行の特定のデータベースでのみを有効にすることはできません。

R スクリプトの CPU およびメモリの使用状況を監視するために使用、DMV sys.dm_db_resource_stats では、プレビュー リリースでは使用できません。

### <a name="other-limitations"></a>その他の制限事項

次の機能がサポートされていません。 

+ MicrosoftML パッケージは使用できません。
+ 外部ライブラリの作成などのパッケージ管理機能がサポートされていません。
+ R クライアントからのスクリプトを実行する場合は、Azure SQL データベースをリモート計算コンテキストとして使用できません。 ストアド プロシージャ sp_execute_external_script を使用して、R スクリプトを実行する必要があります。 ストアド プロシージャが呼び出されるスクリプトは、その他の計算コンテキストを使用できません。
+ Rx 関数を並列実行を必要とする呼び出しを実行することはできません。
+ R スクリプトから SQL Server へのループバック接続はサポートされていません。 言い換えると、R スクリプトから別の ODBC データ ソースへの外部の呼び出しを行うことはできません。

## <a name="get-started"></a>作業を開始します。

SQL Server 開発チームからこのお知らせには、R モデルの構築と予測の生成をテストする、独自の Azure SQL データベースで実行できる短いサンプルが含まれます。

+ [トレーニングと Azure SQL データベースにおけるスコア モデル](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/09/25/announcing-preview-of-machine-learning-services-with-r-support-in-azure-sql-database/)

