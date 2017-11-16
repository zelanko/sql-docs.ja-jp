---
title: "権限の付与処理 (Analysis Services) |Microsoft ドキュメント"
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
- permissions [Analysis Services], process
- process permissions [Analysis Services]
ms.assetid: c1531c23-6b46-46a8-9ba3-b6d3f2016443
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7f1542d477a10e6a77e67e24d607b7086da1bb55
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-process-permissions-analysis-services"></a>処理権限の付与 (Analysis Services)
  管理者は、Analysis Services 処理操作専用のロールを作成して、その特定のタスクを他のユーザーまたは自動スケジューリング処理用のアプリケーションに委任できます。 処理権限はデータベース、キューブ、ディメンション、およびマイニング構造レベルで許可することができます。 非常に大きなキューブまたは表形式データベースで作業している場合を除き、相互に依存関係にあるものなどすべてのオブジェクトを含めて、データベース レベルで処理権限を付与することをお勧めします。  
  
 権限は、オブジェクトを権限および Windows ユーザーアカウントまたはグループ アカウントに関連付けるロールによって付与されます。 権限は加算的であることに注意してください。 あるロールによってキューブを処理する権限が付与され、別のロールによって同じユーザーにディメンションを処理する権限が付与される場合、この 2 種類のロールによる権限が組み合わされ、キューブを処理する権限とそのデータベース内の指定のディメンションを処理する権限の両方がユーザーに付与されます。  
  
> [!IMPORTANT]  
>  ロールによって処理権限のみが付与されているユーザーは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に接続したり、オブジェクトを処理したりすることはできません。 これらのツールを使用するには、オブジェクト メタデータにアクセスするための **定義の読み取り** 権限が必要となります。 どちらのツールも使用できない場合は、XMLA スクリプトを使用して処理操作を実行する必要があります。  
>   
>  また、テスト目的で **定義の読み取り** 権限も付与することをお勧めします。 **定義の読み取り** 権限と **データベースの処理** 権限の両方を持つユーザーは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で対話的にオブジェクトを処理できます。 「 [オブジェクト メタデータに対する定義の読み取り権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md) 」を参照してください。  
  
## <a name="set-processing-permissions-at-the-database-level"></a>データベース レベルでの処理権限の設定  
 ここでは、管理者以外のユーザーがデータベース内のすべてのキューブ、ディメンション、マイニング構造、およびマイニング モデルを処理できるようにする方法について説明します。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。  
  
2.  右クリック**ロール** | **新しいロール**です。 名前と説明を入力します。  
  
3.  **[全般]** ペインで、 **[データベースの処理]** チェック ボックスをオンにします。 また、 **などいずれかの SQL Server ツールで対話型の処理を有効にするには、** [定義の読み取り] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]もオンにします。  
  
4.  **[メンバーシップ]** ペインで、このデータベースのすべてのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックすると、ロール定義が完了します。  
  
## <a name="set-processing-permissions-on-individual-objects"></a>個々のオブジェクトに対する処理権限の設定  
 個々のキューブ、ディメンション、データ マイニング構造、またはデータ マイニング モデルに対する処理権限を設定できます。  
  
 一緒に処理する必要があるオブジェクトを誤って除外した場合は、処理が失敗することがあります (たとえば、キューブに対する処理は有効にしたものの、その関連するディメンションに対する処理は有効にしなかった場合)。 オブジェクトの依存関係は見落とされやすいため、個々のオブジェクトに対する処理権限を設定するときには、徹底的にテストする必要があります。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。  
  
2.  右クリック**ロール** | **新しいロール**です。 名前と説明を入力します。  
  
3.  **[全般]** ペインで、 **[データベースの処理]** チェック ボックスをオフにします。 データベース権限によって、ロールのオプションがグレー表示されるか選択不可になることで、下位レベルのオブジェクトに対する権限の設定機能が上書きされます。  
  
     技術的には、専用の処理ロール用にデータベース権限は必要ありません。 ただし、データベース レベルで **[定義の読み取り]** がないと、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でデータベースを表示することができず、テストが難しくなります。  
  
4.  処理する個々のオブジェクトを選択します。  
  
    -   **[キューブ]** ペインで、各キューブの **[処理]** チェック ボックスをオンにします。  
  
    -   **[ディメンション]** ペインで、 **[すべてのデータベース ディメンション]**を選択し、各ディメンションの **[処理]** チェック ボックスをオンにします。 あるいは、すべての行を選択し、シフトクリックを使用してチェック ボックスの選択を切り替えます。  
  
5.  **[メンバーシップ]** ペインで、これらのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
6.  **[OK]** をクリックすると、ロール定義が完了します。  
  
## <a name="test-processing"></a>処理のテスト  
  
1.  Shift キーを押したまま [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を右クリックし、 **[別のユーザーとして実行する]** を選択し、テスト対象のロールに割り当てられた Windows アカウントを使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。  
  
2.  [データベース] フォルダーを開き、データベースを選択します。 アカウントにメンバーシップが付与されているロールで表示可能なデータベースのみが表示されます。  
  
3.  キューブまたはディメンションを右クリックし、 **[処理]**を選択します。 処理オプションを選択します。 オブジェクトのすべての組み合わせについて、すべてのオプションをテストします。 オブジェクトが見つからないためにエラーが発生した場合は、そのオブジェクトをロールに追加します。  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a>データ マイニング構造に対する処理権限の設定  
 データ マイニング構造を処理するための権限を付与するロールを作成できます。 これには、すべてのマイニング モデルの処理が含まれます。  
  
 マイニング モデルおよびマイニング構造の参照に使用される**[ドリルスルー]** 権限と **[定義の読み取り]** permissions used for browsing a mining model 権限と structure are atomic 権限と can be added to the same role, or separated out into a different role.  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。  
  
2.  右クリック**ロール** | **新しいロール**です。 名前と説明を入力します。 **[全般]** ペインで、データベース権限のチェック ボックスがオフであることを確認します。 データベース権限によって、ロールのオプションがグレー表示されるか選択不可になることで、下位レベルのオブジェクトに対する権限の設定機能が上書きされます。  
  
3.  **[マイニング構造]** ペインで、各マイニング構造の **[処理]** チェック ボックスをオンにします。  
  
4.  **[メンバーシップ]** ペインで、このデータベースのすべてのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックすると、ロール定義が完了します。  
  
## <a name="see-also"></a>参照  
 [データベース、テーブル、またはパーティションの処理 (Analysis Services)](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)   
 [多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [データベース権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)   
 [オブジェクト メタデータに対する定義の読み取り権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  

