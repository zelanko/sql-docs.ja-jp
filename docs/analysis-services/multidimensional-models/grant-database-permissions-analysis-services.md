---
title: "データベース アクセス許可 (Analysis Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [Analysis Services], full control
- full control permissions [Analysis Services]
ms.assetid: be7e5f64-af43-47d6-84a5-c5c1c277d644
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c58a338f700785bb338703c72e3b435a7aa22b94
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-database-permissions-analysis-services"></a>データベース権限の付与 (Analysis Services)
  リレーショナル データベースのバックグラウンドを持つ方が Analysis Services データベース管理を始める場合に、まず理解する必要があることは、データ アクセスの観点で、データベースは Analysis Services の主要なセキュリティ保護可能なオブジェクトではないということです。  
  
 Analysis Services の主要なクエリ構造はキューブ (または表形式モデル) であり、それらの特定のオブジェクトにユーザー権限が設定されます。 リレーショナル データベース エンジンではデータベース ログインおよびユーザー権限 (多くの場合 **db_datareader**) がデータベース自体に対して設定されるのとは対照的に、Analysis Services データベースは大部分がデータ モデルの主要なクエリ オブジェクトのコンテナーとなります。 当面の目的がキューブまたは表形式モデルに対するデータ アクセスを有効にすることである場合、ここではデータベース権限をバイパスし、すぐに次のトピックに進むことができます: [キューブ権限またはモデル権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)。  
  
 Analysis Services のデータベース権限によって、管理機能が使用できるようになります。フル コントロール データベース権限と概要は同じですが、処理操作を委任する場合の粒度が高くなるという特性があります。 Analysis Services データベースの権限レベルは、次の図と説明に示すように、 **[ロールの作成]** ダイアログ ボックスの **[全般]** ペインに指定されています。  
  
 Analysis Services にはログインがありません。 単にロールを作成し、 **[メンバーシップ]** ペインで Windows アカウントを割り当てるだけです。 管理者も含めてすべてのユーザーが、Windows アカウントを使用して Analysis Services に接続します。  
  
 ![データベースの作成のロール ダイアログを表示権限](../../analysis-services/multidimensional-models/media/ssas-permsdbrole.png "ロール ダイアログを示すデータベースのアクセス許可の作成")  
  
 データベース レベルで指定される権限には、3 つの種類があります。  
  
 **フル コントロール (管理者)** : フル コントロールは、Analysis Services データベースに対して幅広い裁量を持つすべてを網羅した権限であり、たとえば、データベース内の任意のオブジェクトに対してクエリまたは処理を実行したり、ロールのセキュリティを管理したりできます。 フル コントロールは、データベース管理者ステータスと同義です。 **［フル コントロール］**を選択すると、 **[データベースの処理]** 権限と **[定義の読み取り]** 権限も同時に選択され、削除できなくなります。  
  
> [!NOTE]  
>  サーバー管理者 (サーバー管理者ロールのメンバー) も、サーバー上のすべてのデータベースに対して、暗黙的にフル コントロールがあります。  
  
 **データベースの処理** : この権限は、データベース レベルで処理を委任するために使用します。 管理者は、別のユーザーまたはサービスにデータベース内の任意のオブジェクトに対する処理操作の呼び出しを許可するロールを作成して、このタスクの負担を軽減できます。 また、特定のオブジェクトに対する処理を可能にするロールも作成できます。 詳細については、「 [処理権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md) 」を参照してください。  
  
 **定義の読み取り** : この権限によって、オブジェクト メタデータを読み取ることができるようになりますが、関連するデータを表示することはできません。 通常、この権限は専用の処理用に作成されたロールで使用され、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] や [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] などのツールを使用してデータベースを対話的に処理できるようにします。 **[定義の読み取り]**権限がない場合、 **[データベースの処理]** 権限は、スクリプト化されたシナリオでのみ有効になります。 SSIS や他のスケジューラなどで処理を自動化する場合は、 **[データベースの処理]** 権限があり、 **[定義の読み取り]**権限がないロールを作成することをお勧めします。 それ以外の場合は、2 つのプロパティを同じロールに結合することで、ユーザー インターフェイスにデータ モデルを視覚化する SQL Server ツールを使用して自動処理と対話型処理の両方をサポートすることを検討してください。  
  
## <a name="full-control-administrator-permissions"></a>フル コントロール (管理者) 権限  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、データベース管理者はフル コントロール (管理者) 権限が含まれているロールに割り当てられた Windows ユーザー ID です。 データベース管理者は、データベース内で次のようなタスクを実行できます。  
  
-   オブジェクトを処理します。  
  
-   キューブ、ディメンション、メジャー グループ、パースペクティブ、データ マイニング モデルなど、データベース内のすべてのオブジェクトのデータおよびメタデータを読み取ります。  
  
-   フル コントロール権限も持つロールにユーザーを追加するなどユーザーまたは権限を追加して、データベース ロールを作成または変更します。  
  
-   データベース ロールまたはロール メンバーシップを削除します。  
  
-   データベースのアセンブリ (またはストアド プロシージャ) を登録します。  
  
 データベース管理者は、サーバー上でデータベースを追加または削除したり、同じサーバー上の他のデータベースに管理者権限を付与したりすることはできません。 その特権は、サーバー管理者にのみ属します。 この権限レベルの詳細については、「 [Analysis Services インスタンスにサーバー管理者権限を付与する](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md) 」を参照してください。  
  
 すべてのロールがユーザー定義であるため、この目的専用のロール (たとえば、"dbadmin" という名前のロール) を作成し、適切な Windows ユーザー アカウントおよびグループ アカウントを割り当てることをお勧めします。  
  
#### <a name="create-roles-in-ssms"></a>SSMS でのロールの作成  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のインスタンスに接続[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を開き、**データベース**フォルダー、データベースを選択し、右クリック**ロール** | **新しいロール**.  
  
2.  **[全般]** ペインで、DBAdmin などのような名前を入力します。  
  
3.  キューブの **[フル コントロール (管理者)]** チェック ボックスをオンにします。 **[データベースの処理]** と **[定義の読み取り]** が自動的に選択されます。 どちらの権限も、 **[フル コントロール]**を含むロールに常に含まれます。  
  
4.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="process-database"></a>[データベースの処理]  
 データベース権限を付与するロールを定義するときは、 **[フル コントロール]** をスキップし、 **[データベースの処理]**のみを選択できます。 この権限はデータベース レベルで設定され、データベース内のすべてのオブジェクトに対する処理を許可します。 詳細については、「 [処理権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
## <a name="read-definition"></a>[定義の読み取り]  
 **[データベースの処理]**と同じく、データベース レベルで **[定義の読み取り]** 権限を設定すると、データベース内の他のオブジェクトに連鎖的に影響を及ぼします。 よりきめ細かいレベルで定義の読み取り権限を設定する場合は、[全般] ペインでデータベース プロパティとして [定義の読み取り] をオフにする必要があります。 詳細については、「[オブジェクト メタデータに対する定義の読み取り権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスにサーバー管理者権限を付与する](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [処理権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
  

