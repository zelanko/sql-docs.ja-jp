---
title: "展開および mrsdeploy を使用して分析を使用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/20/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: b090579bd0a32b901d1c1cedcc26b290d7a68771
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="deploy-and-consume-analytics-using-mrsdeploy"></a>展開および mrsdeploy を使用して分析を使用します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Microsoft R Server には、操作運用の機能が含まれています**mrsdeploy**、これらのタスクをサポートします。

+ 発行および R、Python のモデル、および web サービスの形式でコードを管理します。
+ クライアント アプリケーション内でこれらのサービスの使用

このトピックでは、有効にして、機能を構成する方法に関する情報を提供します。

によってサポートされるシナリオについての一般的な**mrsdeploy**を参照してください[R Server と操作運用](https://docs.microsoft.com/r-server/what-is-operationalization)です。

## <a name="using-mrsdeploy-for-operationalization"></a>Mrsdeploy を操作運用の使用

単語*操作運用*多くのことを意味することができます。

+ アプリケーションで使用するための web サービスにモデルを公開する機能
+ 拡張性の高い、または分散を計算するためのサポート
+ 1 回の開発、何回の展開
+ 両方の単一行の高速のスコアと、バッチ スコアリング

SQL Server で Machine Learning のサービスをインストールした場合*操作運用*ストアド プロシージャで R または Python コードを折り返すの問題です。 任意のアプリケーションでは、モデルを再トレーニング、スコアの生成、またはレポートを作成するストアド プロシージャを呼び出すことができますし、します。 SQL Server の既存のスケジューリング メカニズムを使用してジョブを自動化することもできます。

ただし、Microsoft R Server 別のメカニズムを提供配置のサポート、分散の R ジョブを実行するための R ジョブ、および管理ユーティリティの発行をサポートする web サービスを使用します。 Microsoft R Server 内の関数を使用して、 **mrsdeploy**のパッケージをリモートの計算ノードでセッションを確立して、コンソール アプリケーションで R コードを実行します。

R Server のこの配置機能には、これらの利点があります。

+ 分析の web サービスへのロールベースのアクセス制御

    できますのみ一覧に他のユーザーおよびユーザーによって公開されたおよび web サービスを使用することができますも更新し、web サービスを削除するユーザー、発行、更新、および独自の web サービスを削除することができますを判断します。

+ 高速スコアリング
  
  スコア付けの操作の速度を向上させるためにリアルタイムのサポートされている R モデル オブジェクトにスコア付けを行うこともできます。

+ Web サービスとしての Python コードを発行します。

  例については、次を参照してください。[発行 Python コードを使用すると](./python/publish-consume-python-code.md)です。

+ 非同期のバッチの消費量

  大規模な入力データに対して呼び出す web サービスは、バッチの実行を使用して非同期的にここで使用できます。

+ Web およびコンピューティング ノードのグリッドの自動スケーリング

  スクリプト テンプレートは、簡単に Azure では、R サーバー Vm の一連のスピンアップし、それらを分析およびリモート実行の運用のグリッドとして構成できるように提供されます。 このグリッドは、スケール アップまたは CPU 使用率に基づいて、ダウンできます。

+ 非同期のリモート実行

    使用するようになりました、 **mrsdeploy** R パッケージです。 リモート スクリプト実行時に、開発環境で作業を続行するには、非同期的を使用して、R スクリプトの実行、`async`パラメーター。 これは、実行時間が長いスクリプトを実行しているときに特に便利です。

## <a name="requirements-and-configuration"></a>要件と構成

SQL Server 2017 CTP 2.0 以降には、以前 R Server でのみ利用可能だったし、SQL Server R Services と共にインストールされませんが、この機能が含まれています。 **Mrsdeploy**をインストールするオプションを選択した場合に、SQL Server コンピューターにパッケージがインストールされている**Microsoft Machine Learning Server**から、**共有機能**SQL Server セットアップのセクションです。

通常、SQL Server の Machine Learning のサービスを実行している同じコンピューターには、Machine Learning のサーバーをインストールすることはお勧めできません。 インストールすることをお勧め**Microsoft Machine Learning Server** 、SQL Server から別のコンピューターにし、そのコンピューターで操作運用の機能を構成します。

ただし、それらを一緒にインストールする必要がある場合を正常にサービスを構成するのには、次の追加手順に従います。

1. DotNetCore 1.1 をインストールします。

    SQL Server の一部として .NET Core がインストールされていない場合は、R サーバーのセットアップを開始する前にインストールする必要があります。

2. マイクロソフトの機械学習のサーバーをインストールします。

3. セットアップの完了後**Microsoft Machine Learning サーバー**を手動で、次のレジストリ キーの追加**mrsdeploy**、R_SERVER ファイルの基本フォルダーを指定します。 

    + 新しいレジストリ キーを作成します。`H_KEY_LOCAL_MACHINE\SOFTWARE\R Server\Path`
    + キーの値を設定`"C:\Program Files\Microsoft SQL Server\140\R_SERVER"`です。

4. 終了したら、開く、[管理者ユーティリティ](https://docs.microsoft.com/r-server/operationalize/configure-use-admin-utility)です。

5. 構成を続行、 **mrsdeploy** 」の説明に従ってサービス:[管理者用の構成](https://docs.microsoft.com/r-server/operationalize/configure-start-for-administrators)

6. 詳細については、次を参照してください。 [mrsdeploy 関数](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package)です。
