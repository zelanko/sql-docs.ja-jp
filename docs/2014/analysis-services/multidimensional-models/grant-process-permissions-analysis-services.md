---
title: 権限の付与処理 (Analysis Services) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- permissions [Analysis Services], process
- process permissions [Analysis Services]
ms.assetid: c1531c23-6b46-46a8-9ba3-b6d3f2016443
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1024a8dfbd7bd84db7e452018829b506565badf2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077427"
---
# <a name="grant-process-permissions-analysis-services"></a>処理権限の付与 (Analysis Services)
  管理者は、Analysis Services 処理操作専用のロールを作成して、その特定のタスクを他のユーザーまたは自動スケジューリング処理用のアプリケーションに委任できます。 処理権限はデータベース、キューブ、ディメンション、およびマイニング構造レベルで許可することができます。 非常に大きなキューブまたは表形式データベースで作業している場合を除き、相互に依存関係にあるものなどすべてのオブジェクトを含めて、データベース レベルで処理権限を付与することをお勧めします。  
  
 権限は、オブジェクトを権限および Windows ユーザーアカウントまたはグループ アカウントに関連付けるロールによって付与されます。 権限は加算的であることに注意してください。 あるロールによってキューブを処理する権限が付与され、別のロールによって同じユーザーにディメンションを処理する権限が付与される場合、この 2 種類のロールによる権限が組み合わされ、キューブを処理する権限とそのデータベース内の指定のディメンションを処理する権限の両方がユーザーに付与されます。  
  
> [!IMPORTANT]  
>  ロールによって処理権限のみが付与されているユーザーは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に接続したり、オブジェクトを処理したりすることはできません。 これらのツールが必要な`Read Definition`オブジェクト メタデータにアクセスする権限です。 どちらのツールも使用できない場合は、XMLA スクリプトを使用して処理操作を実行する必要があります。  
>   
>  お勧めするも grant`Read Definition`テスト目的でのアクセス許可。 両方を持つユーザー`Read Definition`と`Process Database`アクセス許可が内のオブジェクトを処理できる[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、対話的にします。 「 [Grant read definition permissions on object metadata &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) 」を参照してください。  
  
## <a name="set-processing-permissions-at-the-database-level"></a>データベース レベルでの処理権限の設定  
 ここでは、管理者以外のユーザーがデータベース内のすべてのキューブ、ディメンション、マイニング構造、およびマイニング モデルを処理できるようにする方法について説明します。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。  
  
2.  右クリック**ロール** | **新しいロール**です。 名前と説明を入力します。  
  
3.  **全般**ペインで、`Process Database`チェック ボックスをオンします。 さらに、選択`Read Definition`など SQL Server ツールのいずれかを通して対話型処理を有効にする[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
4.  **[メンバーシップ]** ペインで、このデータベースのすべてのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックすると、ロール定義が完了します。  
  
## <a name="set-processing-permissions-on-individual-objects"></a>個々のオブジェクトに対する処理権限の設定  
 個々のキューブ、ディメンション、データ マイニング構造、またはデータ マイニング モデルに対する処理権限を設定できます。  
  
 一緒に処理する必要があるオブジェクトを誤って除外した場合は、処理が失敗することがあります (たとえば、キューブに対する処理は有効にしたものの、その関連するディメンションに対する処理は有効にしなかった場合)。 オブジェクトの依存関係は見落とされやすいため、個々のオブジェクトに対する処理権限を設定するときには、徹底的にテストする必要があります。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。  
  
2.  右クリック**ロール** | **新しいロール**です。 名前と説明を入力します。  
  
3.  **全般** ウィンドウで、クリア、`Process Database`チェック ボックスをオンします。 データベース権限によって、ロールのオプションがグレー表示されるか選択不可になることで、下位レベルのオブジェクトに対する権限の設定機能がオーバーライドされます。  
  
     技術的には、専用の処理ロール用にデータベース権限は必要ありません。 せず`Read Definition`データベース レベルでデータベースを表示することはできません[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]テストがより困難です。  
  
4.  処理する個々のオブジェクトを選択します。  
  
    -   **[キューブ]** ペインで、各キューブの **[処理]** チェック ボックスをオンにします。  
  
    -   **[ディメンション]** ペインで、 **[すべてのデータベース ディメンション]** を選択し、各ディメンションの **[処理]** チェック ボックスをオンにします。 あるいは、すべての行を選択し、シフトクリックを使用してチェック ボックスの選択を切り替えます。  
  
5.  **[メンバーシップ]** ペインで、これらのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
6.  **[OK]** をクリックすると、ロール定義が完了します。  
  
## <a name="test-processing"></a>処理のテスト  
  
1.  Shift キーを押したまま [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を右クリックし、 **[別のユーザーとして実行する]** を選択し、テスト対象のロールに割り当てられた Windows アカウントを使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。  
  
2.  [データベース] フォルダーを開き、データベースを選択します。 アカウントにメンバーシップが付与されているロールで表示可能なデータベースのみが表示されます。  
  
3.  キューブまたはディメンションを右クリックし、 **[処理]** を選択します。 処理オプションを選択します。 オブジェクトのすべての組み合わせについて、すべてのオプションをテストします。 オブジェクトが見つからないためにエラーが発生した場合は、そのオブジェクトをロールに追加します。  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a>データ マイニング構造に対する処理権限の設定  
 データ マイニング構造を処理するための権限を付与するロールを作成できます。 これには、すべてのマイニング モデルの処理が含まれます。  
  
 **ドリル スルー**と`Read Definition`マイニング モデルと構造体を参照するために使用される権限はアトミックと同じロールに追加または別のロールを分けることができます。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。  
  
2.  右クリック**ロール** | **新しいロール**です。 名前と説明を入力します。 **[全般]** ペインで、データベース権限のチェック ボックスがオフであることを確認します。 データベース権限によって、ロールのオプションがグレー表示されるか選択不可になることで、下位レベルのオブジェクトに対する権限の設定機能がオーバーライドされます。  
  
3.  **[マイニング構造]** ペインで、各マイニング構造の **[処理]** チェック ボックスをオンにします。  
  
4.  **[メンバーシップ]** ペインで、このデータベースのすべてのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックすると、ロール定義が完了します。  
  
## <a name="see-also"></a>参照  
 [データベースの処理、テーブル、またはパーティション](../tabular-models/process-database-table-or-partition-analysis-services.md)   
 [多次元モデル オブジェクトの処理](processing-a-multidimensional-model-analysis-services.md)   
 [データベースのアクセス許可を付与&#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [読み取りオブジェクト メタデータに対する definition 権限を付与&#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  