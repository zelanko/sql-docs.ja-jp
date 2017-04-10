---
title: "Analysis Services インスタンスにサーバー管理者権限を付与する | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管理権限 [Analysis Services]"
  - "サーバー全体の管理権限 [Analysis Services]"
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# Analysis Services インスタンスにサーバー管理者権限を付与する
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス内のサーバー管理者ロールのメンバーは、そのインスタンスのすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトとデータに制限なくアクセスできます。 データベースの作成または処理、サーバーのプロパティの変更、トレースの起動など、イベントの処理を除くサーバー全体のタスクを実行するためには、ユーザーがサーバー管理者ロールのメンバーである必要があります。  
  
 ロールのメンバーシップは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がインストールされるときに設定されます。 セットアップ プログラムを実行するユーザーは、自分または別のユーザーをロールに追加することができます。 セットアップを続行するには、少なくとも 1 人の管理者を指定する必要があります。  
  
 既定では、ローカルの Administrators グループのメンバーにも、Analysis Services の管理者権限が付与されます。 ローカル グループには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のサーバー管理者ロールのメンバーシップが明示的に付与されているわけではありませんが、ローカル管理者はデータベースの作成、ユーザーとアクセス許可の追加、およびシステム管理者に許可されたその他のタスクを実行できます。 この暗黙的な管理者権限の付与は構成可能です。 この動作は、 **BuiltinAdminsAreServerAdmins** サーバー プロパティによって決まります。このプロパティは既定で **true** に設定されています。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でこのプロパティを変更できます。 詳細については、「 [Security Properties](../../analysis-services/server-properties/security-properties.md)」を参照してください。  
  
 インストール後は、ロールのメンバーシップを変更することで、サービスへの完全な権限を必要とする他のユーザーを追加することができます。 また、分析管理オブジェクト (AMO) を使用してもサーバー ロールを管理できます。 詳細については、「[分析管理オブジェクト (AMO) による開発](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、サーバー、データベース、オブジェクトの各レベルで処理とクエリを行えるように、これまでよりもさらに細かくロールを設定できるようになっています。 これらのロールの使用方法については、「[ロールと権限 (Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)」を参照してください。  
  
## サーバー ロールのメンバーシップの変更  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続し、オブジェクト エクスプローラーでそのインスタンス名を右クリックして、**[プロパティ]** をクリックします。  
  
2.  **[ページの選択]** ペインで **[セキュリティ]** をクリックし、ページの下部にある **[追加]** をクリックして、サーバー ロールに 1 つまたは複数の Windows ユーザーまたはグループを追加します。  
  
     ![Management Studio にユーザー ダイアログ ボックスを追加](../../analysis-services/instances/media/ssas-serveradminadd.png "Management Studio にユーザー ダイアログ ボックスを追加")  
  
### コンピューター アカウントの追加  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、コンピューター アカウントを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理者グループのメンバーに設定することもできます。  
  
1.  **[ユーザーとグループの選択]** ダイアログの **[場所]**をクリックします。  
  
2.  追加するコンピューターが属しているドメインを選択するか、 **[ディレクトリ全体]** を選択して **[OK]**をクリックします。  
  
3.  **[オブジェクトの種類]**をクリックします。  
  
4.  **[コンピューター]** を選択し、 **[OK]**をクリックします。  
  
     ![add computer accounts as ssas administrators](../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "add computer accounts as ssas administrators")  
  
5.  **[選択するオブジェクト名を入力してください]** ボックスにコンピューターの名前を入力し、 **[名前の確認]** をクリックして、コンピューター アカウントが現在の場所で見つかることを確認します。 コンピューター アカウントが見つからない場合は、コンピューター名と、そのコンピューターが属している実際のドメインを確認してください。  
  
## NT Service\SSASTelemetry アカウント  
 **NT Service/SSASTelemetry** は、権限の低いコンピューター アカウントです。セットアップ中に作成され、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で実装されているカスタマー エクスペリエンス向上プログラム (CEIP) サービスの実行にのみ使用されます。 このサービスは、いくつかの discover コマンドを実行するために [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上で管理者権限を必要とします。 詳細については、「 [Customer Experience Improvement Program for SQL Server Data Tools](../../sql-server/customer-experience-improvement-program-for-sql-server-data-tools.md) 」および「 [Microsoft SQL Server Privacy Statement](../Topic/Microsoft%20SQL%20Server%20Privacy%20Statement.md) 」を参照してください。  
  
## 参照  
 [オブジェクトと操作へのアクセスの承認 (Analysis Services)](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [セキュリティ ロール (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  