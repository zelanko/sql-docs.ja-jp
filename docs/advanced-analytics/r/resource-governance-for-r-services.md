---
title: "R Services のリソース管理 | Microsoft Docs"
ms.custom: 
ms.date: 05/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c9978a-aa55-42bd-9ab3-8097030888c9
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5475c2258971c48c2e19bba69d9ec962ae48be87
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="resource-governance-for-r-services"></a>R Services のリソース管理
  R の問題点の 1 つは、実稼働環境の大容量データを分析するために追加のハードウェアが必要になることです。また、多くの場合、データベースから IT で制御されないコンピューターにデータが移動されます。  高度な分析処理を実行するため、お客様はデータベース サーバー リソースを活用することを望みます。データを保護するためには、このような処理がセキュリティやパフォーマンスに関してエンタープライズ レベルのコンプライアンス要件を満たす必要があります。  
  
 このセクションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを計算コンテキストとして使用して、R ランタイムおよび R ジョブで使用されるリソースを管理する方法を説明します。  
  
## <a name="what-is-resource-governance"></a>リソース管理とは  
 リソース管理の目的は、データベース サーバー環境で一般的な問題を特定して防ぐことです。このような環境には多くの場合、複数の依存アプリケーション、サポートや負荷分散を行う複数のサービスがあります。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の場合、リソース管理には次のタスクが含まれます。  
  
-   サーバー リソースを過剰に使用するスクリプトの特定  
  
     管理者は、消費するリソースが多すぎるジョブを停止または調整できる必要があります。  
  
-   予測できないワークロードの軽減  
  
     たとえば、複数の R ジョブがサーバーで同時に実行しており、ジョブがリソース プールを使用して互いに分離されていない場合は、結果としてリソース競合が発生し、予測できないパフォーマンスにつながったり、ワークロードの完了を脅かしたりする可能性があります。  
  
-   ワークロードの優先順位付け  
  
     管理者または設計者は、優先されるワークロードを指定したり、リソース競合が発生した際に特定のワークロードの完了を保証したりできることが必要です。  
  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)を使用して、R ランタイムとリモート R ジョブで使用されるリソースを管理できます。  
  
## <a name="how-to-use-resource-governor-to-manage-r-jobs"></a>リソース ガバナーを使用して R ジョブを管理する方法  
 一般に、R ジョブに割り当てられたリソースを管理するには、"*外部リソース プール*" を作成して、ワークロードをプール (1 つまたは複数) に割り当てます。 外部リソース プールは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に導入された新しい種類のリソース プールです。データベース エンジン外部の R ランタイムやその他のプロセスの管理に役立ちます。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には現在 3 種類の既定リソース プールがあります。  
  
-   "*内部プール*" は、SQL Server そのもので使用されるリソースを表します。変更または制限することはできません。  
  
-   "*既定プール*" は定義済みのユーザー プールです。サーバー全体のリソース使用を変更するために使用できます。 このプールに属するユーザー グループを定義して、リソースへのアクセスを管理することもできます。  
  
-   "*既定外部プール*" は、外部リソース用の定義済みユーザー プールです。 また、新しく外部リソース プールを作成して、そのプールに属するユーザー グループを定義できます。  
  
 さらに、"*ユーザー定義リソース グループ*" を作成して、リソースをデータベース エンジンまたは他のアプリケーションに割り当てることや、"*ユーザー定義外部リソース プール*" を作成して R やその他の外部プロセスを管理することができます。  
  
 用語および一般的な概念について詳しくは、「[Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md)」(リソース ガバナーのリソース プール) をご覧ください。  

  
## <a name="resource-management-using-resource-governor"></a>リソース ガバナーを使用したリソース管理 

   リソース ガバナーを初めて使用する場合は、インスタンスの既定リソースの変更方法や新しい外部リソース プールの作成方法のチュートリアルとして、「[How To: Create a Resource Pool for R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)」(方法: R のリソース プールを作成する) をご覧ください。   
  
 "*外部リソース プール*" メカニズムを使用して、次の R 実行可能ファイルによって使用されるリソースを管理できます。  
  
-   Rterm.exe およびサテライト プロセス  
  
-   BxlServer.exe およびサテライト プロセス  
  
-   スタート パッドで起動されたサテライト プロセス  
  
 ただし、リソース ガバナーによるスタート パッド サービスの直接管理はサポートされません。 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] は信頼済みサービスであり、仕様により Microsoft 提供のランチャーしかホストできないためです。 信頼済みランチャーも、リソースを過度に消費しないように構成できます。  
  
 リソース ガバナーを使用して、サテライト プロセスを管理し、個々のデータベース構成とワークロードのニーズを満たすように調整することをお勧めします。  たとえば、個々のサテライト プロセスは実行中に要求時に作成または破棄することができます。  
  
## <a name="disable-external-script-execution"></a>外部スクリプト実行の無効化  
 外部スクリプトのサポートは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップではオプションです。 [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] をインストールした後でも、外部スクリプトを実行する機能は既定でオフになっています。スクリプトの実行を有効にするには、プロパティを手動で再構成し、インスタンスを再起動する必要があります。  
  
 このため、直ちに軽減する必要があるリソースの問題あるいはセキュリティの問題がある場合、管理者は [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用し、プロパティ `external scripts enabled` を FALSE または 0 に設定することで、外部スクリプトの実行をすぐに無効化できます。  
  
## <a name="see-also"></a>参照  
 [R ソリューションの管理と監視](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
 [R 用のリソース プールを作成する方法](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)  
 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
  


