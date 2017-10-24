---
title: "Python のリソース管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4f83d62804803b2b9f3f028c48a7ec23d3f8d910
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="resource-governance-for-python"></a>Python のリソース管理

Python を使用しているため、SQL Server 2016 での R 言語が実装された同じ拡張可能アーキテクチャ、する既存ツールを使用してリソース ガバナー、Dmv の拡張イベントなどの SQL Server の Python の実行を監視SQL Server でスクリプトを作成します。

具体的には大量の実稼働環境でデータを分析することができます税金の面でも高度なハードウェアのためリソース ガバナンスが重要です。  データ移動できないように、データベース外部の管理も監査がする可能性がありますいないを実行するコンピューターには、データベース管理者が高度な分析操作用に十分なリソースを割り当てることが必要があります。

このセクションでは Python ランタイムによって使用されているリソースを管理する方法に関する情報を提供し、Python でリソースの使用状況の監視スクリプトで実行するジョブ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。

> [!NOTE]
> Python のサポートは新機能で SQL Server 2017 されプレリリース版。 詳細についてはすぐに参照してください。
> 一般に、Python を実行している 1 つを含む、SQL Server 2016 での R スクリプトのリソース ガバナンスのために提供された同じフレームワークを使用して、外部のスクリプトを監視できます。

## <a name="what-is-resource-governance"></a>リソース管理とは

リソース管理の目的は、データベース サーバー環境で一般的な問題を特定して防ぐことです。このような環境には多くの場合、複数の依存アプリケーション、サポートや負荷分散を行う複数のサービスがあります。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の場合、リソース管理には次のタスクが含まれます。  

+ **過剰なサーバー リソースを使用するスクリプトを識別する**です。 管理者は、消費するリソースが多すぎるジョブを停止または調整できる必要があります。

+ **予期しないワークロードを軽減する**です。 Python の複数のジョブがサーバーに同時に実行するリソース プールを使用して、ジョブが互いから分離されていない場合は、結果として得られるリソースの競合が発生する予期しないパフォーマンスまたはワークロードの完了を脅かすできませんでした。

+ **ワークロードの優先順位付け**です。 管理者または設計者は、優先されるワークロードを指定したり、リソース競合が発生した際に特定のワークロードの完了を保証したりできることが必要です。

使用することができます[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)を外部のランタイムで使用したリソースを管理します。 これには、リモートから起動したターミナルは、計算コンテキストとして、SQL Server コンピューターを使用して実行された Python スクリプトが含まれます。

> [!NOTE] 
> リソース ガバナーでは、Enterprise Edition で使用します。

## <a name="how-to-use-resource-governor-to-manage-python-execution"></a>リソース ガバナーを使用して、Python の実行を管理する方法

一般に、作成することで、任意の外部スクリプトのジョブに割り当てられたリソースを管理する、*外部リソース プール*ワークロードをプールに割り当てるとします。 外部リソース プールでは、R ランタイムと、データベース エンジンの外部の他のプロセスを管理するために、SQL Server 2016 で導入されたリソース プールの新しい型です。 以降では、SQL Server 2017 Python ジョブを監視するために使用されます。

既定のリソース プールの次の 3 つの種類があります。

+ "*内部プール*" は、SQL Server そのもので使用されるリソースを表します。変更または制限することはできません。
+ "*既定プール*" は定義済みのユーザー プールです。サーバー全体のリソース使用を変更するために使用できます。 このプールに属するユーザー グループを定義して、リソースへのアクセスを管理することもできます。
+ "*既定外部プール*" は、外部リソース用の定義済みユーザー プールです。 また、新しく外部リソース プールを作成して、そのプールに属するユーザー グループを定義できます。

さらに、"*ユーザー定義リソース グループ*" を作成して、リソースをデータベース エンジンまたは他のアプリケーションに割り当てることや、"*ユーザー定義外部リソース プール*" を作成して R やその他の外部プロセスを管理することができます。

用語および一般的な概念について詳しくは、「[Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md)」(リソース ガバナーのリソース プール) をご覧ください。

## <a name="resource-management-using-resource-governor"></a>リソース ガバナーを使用したリソース管理

リソース ガバナーを初めて使用する場合は、インスタンスの既定リソースの変更方法や新しい外部リソース プールの作成方法のチュートリアルとして、「[How To: Create a Resource Pool for R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)」(方法: R のリソース プールを作成する) をご覧ください。

使用することができます、*外部リソース プール*次のサポートされている実行可能ファイルで使用したリソースを管理するためのメカニズム。

+ SQL Server から呼び出されたか、リモート計算コンテキストとして SQL Server のリモートで呼び出されたときに Python35.exe
+ BxlServer.exe およびサテライト プロセス
+ スタート パッド、PythonLauncher.dll などによって開始されたランチャー

> [!NOTE]
> リソース ガバナーを使用して、スタート パッド サービスのダイレクト管理はサポートされていません。 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] は信頼済みサービスであり、仕様により Microsoft 提供のランチャーしかホストできないためです。 信頼済みランチャーも、リソースを過度に消費しないように構成できます。

リソース ガバナーを使用して、サテライト プロセスを管理し、個々のデータベース構成とワークロードのニーズを満たすように調整することをお勧めします。  たとえば、個々のサテライト プロセスは実行中に要求時に作成または破棄することができます。

## <a name="disable-or-enable-external-script-execution"></a>外部スクリプトの実行を有効または無効に

外部スクリプトのサポートが省略可能で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップ、およびセットアップが完了したら、外部スクリプトの実行後でもは OFF に設定の既定のセキュリティ上の理由。 そのため、機械学習の言語および関連するサービスのいずれかのインストールが完了したら後のインスタンスを明示的に再構成して、データベース エンジン サービスを再起動します。

ランナウェイのスクリプトが発生した場合に、すべてのスクリプトの実行を無効にすることができます。 この処理を取り消すし、プロパティを設定するだけ`external scripts enabled`FALSE、またはインスタンス上の 0 にします。 任意の外部スクリプトの実行直後に無効になります。 このオプションのセキュリティ問題、またはすぐにリソースの問題を軽減するために、管理者が必要な状況を予約する必要があります。

## <a name="see-also"></a>参照

[リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)


