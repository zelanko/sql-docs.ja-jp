---
title: "R のサービスのリソース管理 | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18c9978a-aa55-42bd-9ab3-8097030888c9
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# R のサービスのリソース管理
  R での 1 つの問題点は、大量の実稼働環境でのデータを分析する追加のハードウェアと多くの場合、そのデータを移動、データベースの外部で制御されていないコンピューターに IT です。  高度な分析操作を実行するには、顧客をデータベース サーバーのリソースを利用し、データを保護するがこのような操作が、セキュリティやパフォーマンスなどのエンタープライズ レベルのコンプライアンス要件を満たしている必要なします。  
  
 このセクションでは、R のジョブを使用して実行して、R ランタイムによって使用されているリソースを管理する方法に関する情報を提供、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 計算コンテキストとインスタンス。  
  
## リソースのガバナンスとは何ですか。  
 識別し、複数の依存アプリケーションが多くの場合、複数のサービスをサポートし、分散データベース サーバー環境で見られる問題を回避するのには、リソースのガバナンスは設計されています。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、リソース管理には、これらの作業が必要になります。  
  
-   サーバーに過度なリソースを使用するスクリプトを識別します。  
  
     管理者は、終了または過剰なリソースを消費しているジョブを調整できる必要があります。  
  
-   予測不能なワークロードを軽減します。  
  
     など、サーバーで複数の R のジョブが同時に実行すると、リソース プールを使用して、ジョブの互いに分離されていません、結果のリソースの競合は予測不可能なパフォーマンスにつながるまたはワークロードの完了を脅かすがします。  
  
-   ワークロードの優先順位付けします。  
  
     管理者や設計者は、優先またはリソースの競合がある場合を実行する特定のワークロードを保証する必要があるワークロードを指定できる必要があります。  
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、使用する [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) R ランタイムおよび R のジョブをリモートで使用するリソースを管理します。  
  
## 管理の R のジョブをする方法を使用してリソース ガバナー  
 一般に、作成することで、R のジョブに割り当てられたリソースを管理する *外部のリソース プール* をプールまたはプールのワークロードに割り当てるとします。 外部のリソース プールは、新しい種類のリソース プールで導入された [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], 、R ランタイムおよびデータベース エンジンの外部の他のプロセスを管理するためにします。  
  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], はこれで、既定のリソース プールの 3 種類があります。  
  
-    *内部プール* リソース SQL Server 自体で使用される、変更またはできません制限を表します。  
  
-    *既定のプール* 、サーバーの全体のリソースの使用を変更に使用できる定義済みのユーザー プールです。 リソースへのアクセスを管理するこのプールに属しているユーザー グループを定義することもできます。  
  
-    *デフォルト外部プール* 外部リソースの定義済みのユーザー プールです。 また、新しい外部のリソース プールを作成し、このプールに属しているユーザー グループを定義します。  
  
 さらに、作成 *ユーザー定義のリソース プール* を作成、データベース エンジンまたはその他のアプリケーションへのリソースを割り当てて *ユーザー定義の外部リソース プール* R、およびその他の外部のプロセスを管理します。  
  
 用語と一般的な概念を適切な概要については、次を参照してください。 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)します。  
  
> [!NOTE]  
>  新しいリソース ガバナーのプロパティは DDL ステートメントまたはスクリプトでのみ使用できる現在ユーザー インターフェイスを使用して外部のリソース グループを作成できません [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。  
  
## リソース ガバナーを使用してリソースの管理 

   リソース ガバナーを新しい場合は、インスタンスの既定のリソースを変更し、新しい外部のリソース プールを作成する方法の手順については、このトピックを参照してください:  [How To: R のリソース プールの作成](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)   
  
 使用することができます、 *外部のリソース プール* 次の R 実行可能ファイルで使用したリソースを管理するためのメカニズム。  
  
-   Rterm.exe およびサテライト プロセス  
  
-   BxlServer.exe およびサテライト プロセス  
  
-   スタート パッドで起動されたサテライト プロセス  
  
 ただし、リソース ガバナーを使用して、スタート パッド サービスのダイレクト管理することはサポートされていません。  [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] 設計できる信頼されたサービスが Microsoft によって提供されるランチャーのみをホストします。 信頼されている起動ツールは、リソースを過剰に消費しないようにも構成されます。  
  
 リソース ガバナーを使用してサテライト プロセスを管理して個々 のデータベースの構成やワークロードのニーズに合わせて調整することをお勧めします。  たとえば、各サテライト プロセスを作成または実行中に、要求時に破棄されます。  
  
## 外部スクリプト実行を無効にします。  
 外部スクリプトのサポートが省略可能で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップします。 インストールされた後も [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], 既定では、外部のスクリプトを実行する機能は OFF です。、および手動でプロパティを再構成し、スクリプトの実行を有効にするインスタンスを再起動する必要があります。  
  
 そのため場合、すぐに軽減する必要があるリソースの問題またはセキュリティ上の問題は、管理者はすぐに無効にできますいずれかの外部スクリプト実行を使用して [sp_configure & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) プロパティを設定および `external scripts enabled` FALSE、または 0 にします。  
  
## 参照  
 [R ソリューションの管理と監視](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
 [R のリソース プールを作成する方法](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)  
 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
  