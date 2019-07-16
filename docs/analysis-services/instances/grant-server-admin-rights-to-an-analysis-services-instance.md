---
title: Analysis Services インスタンスにサーバー管理者権限の付与 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e437507d139959c21f723f8a674ca4879570339f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181550"
---
# <a name="grant-server-admin-rights-to-an--analysis-services-instance"></a>Analysis Services インスタンスにサーバー管理者権限を付与する
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス内のサーバー管理者ロールのメンバーは、そのインスタンスのすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトとデータに制限なくアクセスできます。 データベースの作成または処理、サーバーのプロパティの変更、トレースの起動など、イベントの処理を除くサーバー全体のタスクを実行するためには、ユーザーがサーバー管理者ロールのメンバーである必要があります。  
  
 ロールのメンバーシップは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がインストールされるときに設定されます。 セットアップ プログラムを実行するユーザーは、自分または別のユーザーをロールに追加することができます。 セットアップを続行するには、少なくとも 1 人の管理者を指定する必要があります。  
  
 既定では、ローカルの Administrators グループのメンバーにも、Analysis Services の管理者権限が付与されます。 ローカル グループには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のサーバー管理者ロールのメンバーシップが明示的に付与されているわけではありませんが、ローカル管理者はデータベースの作成、ユーザーとアクセス許可の追加、およびシステム管理者に許可されたその他のタスクを実行できます。 この暗黙的な管理者権限の付与は構成可能です。 この動作は、 **BuiltinAdminsAreServerAdmins** サーバー プロパティによって決まります。このプロパティは既定で **true** に設定されています。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でこのプロパティを変更できます。 詳細については、「 [Security Properties](../../analysis-services/server-properties/security-properties.md)」を参照してください。  
  
 インストール後は、ロールのメンバーシップを変更することで、サービスへの完全な権限を必要とする他のユーザーを追加することができます。 また、分析管理オブジェクト (AMO) を使用してもサーバー ロールを管理できます。 詳細については、「[分析管理オブジェクト (AMO) による開発](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、サーバー、データベース、オブジェクトの各レベルで処理とクエリを行えるように、これまでよりもさらに細かくロールを設定できるようになっています。 これらのロールの使用方法については、「[ロールと権限 (Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)」を参照してください。  
  
## <a name="modify-server-role-membership"></a>サーバー ロールのメンバーシップの変更  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーでそのインスタンス名を右クリックして、 **[プロパティ]** をクリックします。  
  
2.  **[ページの選択]** ペインで **[セキュリティ]** をクリックし、ページの下部にある **[追加]** をクリックして、サーバー ロールに 1 つまたは複数の Windows ユーザーまたはグループを追加します。  
  
     ![Management studio で、追加のユーザー ダイアログ ボックス](../../analysis-services/instances/media/ssas-serveradminadd.png "management studio で、追加のユーザー ダイアログ ボックス")  
  
### <a name="add-computer-accounts"></a>コンピューター アカウントの追加  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、コンピューター アカウントを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理者グループのメンバーに設定することもできます。  
  
1.  **[ユーザーとグループの選択]** ダイアログの **[場所]** をクリックします。  
  
2.  追加するコンピューターが属しているドメインを選択するか、 **[ディレクトリ全体]** を選択して **[OK]** をクリックします。  
  
3.  **[オブジェクトの種類]** をクリックします。  
  
4.  **[コンピューター]** を選択し、 **[OK]** をクリックします。  
  
     ![ssas の管理者としてコンピューター アカウントを追加](../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "ssas 管理者としてコンピューター アカウントを追加")  
  
5.  **[選択するオブジェクト名を入力してください]** ボックスにコンピューターの名前を入力し、 **[名前の確認]** をクリックして、コンピューター アカウントが現在の場所で見つかることを確認します。 コンピューター アカウントが見つからない場合は、コンピューター名と、そのコンピューターが属している実際のドメインを確認してください。  
  
## <a name="nt-servicessastelemetry-account"></a>NT Service\SSASTelemetry アカウント  
 **NT Service/SSASTelemetry** は、権限の低いコンピューター アカウントです。セットアップ中に作成され、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で実装されているカスタマー エクスペリエンス向上プログラム (CEIP) サービスの実行にのみ使用されます。 このサービスは、いくつかの discover コマンドを実行するために [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上で管理者権限を必要とします。 詳細については、「 [Customer Experience Improvement Program for SQL Server Data Tools](../../sql-server/customer-experience-improvement-program-for-sql-server-data-tools.md) 」および「 [Microsoft SQL Server Privacy Statement](http://go.microsoft.com/fwlink/?LinkID=868444) 」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクトと操作へのアクセスの承認 (Analysis Services)](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [セキュリティ ロール (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
