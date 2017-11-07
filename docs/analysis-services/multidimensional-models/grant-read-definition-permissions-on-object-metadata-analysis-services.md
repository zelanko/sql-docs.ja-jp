---
title: "Grant 定義の読み取りアクセス許可オブジェクトのメタデータ (Analysis Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 55c4e6d43ffedd933e968e8fc2355871c698d290
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>オブジェクト メタデータに対する定義の読み取り権限の付与 (Analysis Services)
  管理者は、選択したオブジェクトのオブジェクト定義またはメタデータを読み取る権限を使用して、オブジェクトの定義の変更、オブジェクトの構造の変更、またはオブジェクトの実際のデータの表示を行う権限を付与することなく、オブジェクト情報を表示する権限を付与できます。 **[定義の読み取り]** 権限は、データベース、データ ソース、ディメンション、マイニング構造、マイニング モデルの各レベルで付与できます。 キューブの **[定義の読み取り]** 権限が必要である場合は、データベースの **[定義の読み取り]** を有効にする必要があります。権限は加算的であることに注意してください。 たとえば、あるロールではキューブのメタデータを読み取るための権限を付与し、別のロールでは同じユーザーにディメンションのメタデータを読み取るための権限を付与します。 これら 2 つの異なるロールの権限は組み合わされ、キューブのメタデータを読み取る権限と、そのデータベース内のディメンションのメタデータを読み取る権限をユーザーに与えることになります。  
  
> [!NOTE]  
>  データベースのメタデータを読み取る権限は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]データベースに接続するために必要な最小限の権限です。 また、メタデータを読み取る権限を持つユーザーは、DISCOVER_XML_METADATA スキーマ行セットを使用して、オブジェクトのクエリを行い、そのメタデータを表示できます。 詳細については、「 [DISCOVER_XML_METADATA 行セット](../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)」を参照してください。  
  
## <a name="set-read-definition-permissions-on-a-database"></a>データベースに対する定義の読み取り権限の設定  
 データベース メタデータを読み取る権限を付与すると、データベース内のすべてのオブジェクトのメタデータを読み取るための権限も付与されます。  
  
 専用の処理のためのロールを設定する場合は、データベース レベルで **[定義の読み取り]** 権限を含めることをお勧めします。 **[定義の読み取り]** があると、管理者以外のユーザーでも [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でモデルのオブジェクト階層を表示し、個々のオブジェクトに移動して後続の処理を実行できるようになります。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーで適切なデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、新しいデータベース ロールを作成します。  
  
2.  **[全般]** タブで **[定義の読み取り]** オプションを選択します。  
  
3.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
4.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>個々のオブジェクトに対する定義の読み取り権限の設定  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、 **[データベース]** フォルダーを開き、データベースを選択します。オブジェクト エクスプローラーでそのデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、または新しいデータベース ロールを作成します。  
  
2.  **[全般]** ペインで、 **[定義の読み取り]**のデータベース権限を消去します。 この手順によって、権限継承が削除され、個々のオブジェクトに対する権限を設定できるようになります。  
  
3.  **[定義の読み取り]** プロパティを指定するオブジェクトを選択します。  
  
    -   **[データ ソース]** ペインで、そのデータ ソースの **[定義の読み取り]** チェック ボックスをオンにします。 ロール メンバーは、サーバー名や場合によってはユーザー名も含め、データ ソースの接続文字列を表示できます。 接続文字列を変更する権限やその他のオブジェクトの定義を表示する権限は付与しないで、接続文字列情報を提供する場合に、この権限が使用できます。  
  
    -   **[ディメンション]** ペインで、そのディメンションの **[定義の読み取り]** チェック ボックスをオンにします。 熟練したアナリストおよび開発者が、変更権限のない定義を表示したり、他のオブジェクト (他のディメンション、キューブ オブジェクト、マイニング構造、マイニング モデルなど) の定義を表示したりすることが必要になる場合があります。  
  
    -   [マイニング構造] ペインで、データ マイニング構造またはデータ マイニング モデルの **[定義の読み取り]** チェック ボックスをオンにします。 データ モデルを参照するには、**[定義の読み取り]** が必要です。 詳細については、「[データ マイニング構造およびデータ マイニング モデルに対する権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)」を参照してください。  
  
4.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="see-also"></a>参照  
 [データベース権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)   
 [処理権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
  

