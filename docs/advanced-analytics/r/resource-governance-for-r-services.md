---
title: "SQL Server での機械学習用リソース ガバナンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c9978a-aa55-42bd-9ab3-8097030888c9
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 9da686f7284de16d93ded4c87ddfe89e17492a57
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>SQL Server での機械学習用リソース ガバナンス

この記事は、リソース管理の概要を割り当てるし、R と Python スクリプトによって使用されているリソースのバランスをとるに役立つ SQL Server の機能を提供します。

**適用されます:** [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)] 
 [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]と[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)][!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]

## <a name="goals-of-resource-governance-for-machine-learning"></a>機械学習用リソース ガバナンスの目的

1 つの R、Python などの machine learning 言語と既知の問題点はデータがによって制御されていないコンピューターに移動、データベース外部の多くの場合、IT です。 別は R がシングル スレッドで、メモリ内で使用できるデータでのみ作業できることを意味します。 

SQL Server の Machine Learning のサービスは、これら両方の問題を軽減し、企業のコンプライアンス要件を満たすのに役立ちます。 データベース内の高度な分析を保持し、ストリーミングと操作のチャンキングなどの機能を通じて、大規模なデータセットに対するパフォーマンスの向上をサポートします。 ただし、データベース内 R、Python の計算を移動正規ユーザー クエリ、外部アプリケーションは、データベースのスケジュールされたジョブなどのデータベースを使用する他のサービスのパフォーマンスに影響することができます。

このセクションでは、他のコア データベース サービスへの影響を軽減するために、R、Python などの外部のランタイムによって使用されているリソースを管理する方法に関する情報を提供します。 通常、データベース サーバーの環境は、複数の依存アプリケーションとサービスのハブです。

使用することができます[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) R、Python の外部のランタイムで使用したリソースを管理します。  機械学習には、リソース管理には、これらのタスクが含まれます。

+ サーバー リソースを過剰に使用するスクリプトの特定
  
     管理者は、消費するリソースが多すぎるジョブを停止または調整できる必要があります。
  
+ 予測できないワークロードの軽減
  
     たとえば場合 machine learning の複数のジョブは、同時に、サーバー上で実行している、結果として得られるリソースの競合でしたまたはする可能性予期しないパフォーマンス、ワークロードの完了が脅かされることです。 ただし、リソース プールを使用している場合、ジョブは互いから分離のようにできます。
  
-   ワークロードの優先順位付け
  
     管理者や設計者は、優先、またはリソースの競合が発生するときに行う特定のワークロードを保証する必要があるワークロードを指定することである必要があります。

## <a name="how-to-use-resource-governor-to-manage-machine-learning"></a>リソース ガバナーを使用して、機械学習を管理する方法
 
作成することで R または Python のセッションに割り当てられたリソースを管理する、*外部リソース プール*、プールまたはプールにワークロードを割り当てるとします。 外部リソース プールは、新しいリソース プールの種類で導入された[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]R ランタイムとその他の管理に役立つ、外部データベース エンジンに処理します。

SQL Server では、既定のリソース プールの次の 3 つの種類をサポートします。 
  
-   "*内部プール*" は、SQL Server そのもので使用されるリソースを表します。変更または制限することはできません。
  
-   "*既定プール*" は定義済みのユーザー プールです。サーバー全体のリソース使用を変更するために使用できます。 このプールに属するユーザー グループを定義して、リソースへのアクセスを管理することもできます。
  
-   "*既定外部プール*" は、外部リソース用の定義済みユーザー プールです。 また、新しく外部リソース プールを作成して、そのプールに属するユーザー グループを定義できます。
  
 さらに、"*ユーザー定義リソース グループ*" を作成して、リソースをデータベース エンジンまたは他のアプリケーションに割り当てることや、"*ユーザー定義外部リソース プール*" を作成して R やその他の外部プロセスを管理することができます。
  
 用語および一般的な概念について詳しくは、「[Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md)」(リソース ガバナーのリソース プール) をご覧ください。

  
## <a name="resource-management-walkthrough-with-resource-governor"></a>リソース管理のチュートリアルをリソース ガバナー

リソース ガバナーを新しい場合は、インスタンスの既定のリソースを変更し、新しい外部リソース プールを作成する方法の簡単なチュートリアルについては、このトピックを参照してください:[外部スクリプトのリソース プールの作成](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)
  
 使用することができます、*外部リソース プール*機械学習で使用されている次の実行可能ファイルで使用したリソースを管理するためのメカニズム。

+ Rterm.exe およびサテライト プロセス
+ Python.exe およびサテライト プロセス
+ BxlServer.exe およびサテライト プロセス
+ スタート パッドを起動するサテライト プロセス
  
> [!NOTE]
> 
> リソース ガバナーを使用して、スタート パッド サービスのダイレクト管理はサポートされていません。 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] は信頼済みサービスであり、仕様により Microsoft 提供のランチャーしかホストできないためです。 信頼されたランチャーが過剰にリソースを消費しないように構成されます。
>   
> リソース ガバナーを使用して、サテライト プロセスを管理し、個々のデータベース構成とワークロードのニーズを満たすように調整することをお勧めします。  たとえば、個々のサテライト プロセスは実行中に要求時に作成または破棄することができます。
  
## <a name="disable-external-script-execution"></a>外部スクリプトの実行を無効にします。

外部スクリプトのサポートは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップではオプションです。 機械学習機能をインストールした後でも、既定では、外部スクリプトを実行する機能は OFF です。 し、手動でプロパティを再構成し、スクリプトの実行を有効にするインスタンスを再起動する必要があります。

そのため、すぐに、軽減する必要があるリソースの問題またはセキュリティ上の問題がある場合、管理者直ちにを無効にできます、外部スクリプトの実行を使用して[sp_configure &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)プロパティを設定および`external scripts enabled`FALSE または 0 にします。
  
## <a name="see-also"></a>参照

[Machine Learning ソリューションの管理と監視](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

[Machine Learning 用のリソース プールの作成](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

[リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
