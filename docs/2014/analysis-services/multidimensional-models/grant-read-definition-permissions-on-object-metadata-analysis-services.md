---
title: オブジェクトメタデータに対する定義の読み取り権限の付与 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92edbbb45438622566b240d6c600428dff61ac96
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546624"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>オブジェクト メタデータに対する定義の読み取り権限の付与 (Analysis Services)
  管理者は、選択したオブジェクトのオブジェクト定義またはメタデータを読み取る権限を使用して、オブジェクトの定義の変更、オブジェクトの構造の変更、またはオブジェクトの実際のデータの表示を行う権限を付与することなく、オブジェクト情報を表示する権限を付与できます。 `Read Definition`権限は、データベース、データソース、ディメンション、マイニング構造、およびマイニングモデルレベルで許可できます。 キューブに対する権限が必要な場合は、 `Read Definition` データベースに対してを有効にする必要があり `Read Definition` ます。アクセス許可は付加的なものであることに注意してください。 たとえば、あるロールではキューブのメタデータを読み取るための権限を付与し、別のロールでは同じユーザーにディメンションのメタデータを読み取るための権限を付与します。 これら 2 つの異なるロールの権限は組み合わされ、キューブのメタデータを読み取る権限と、そのデータベース内のディメンションのメタデータを読み取る権限をユーザーに与えることになります。  
  
> [!NOTE]  
>  データベースのメタデータを読み取る権限は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]データベースに接続するために必要な最小限の権限です。 また、メタデータを読み取る権限を持つユーザーは、DISCOVER_XML_METADATA スキーマ行セットを使用して、オブジェクトのクエリを行い、そのメタデータを表示できます。 詳細については、「 [DISCOVER_XML_METADATA 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset)」を参照してください。  
  
## <a name="set-read-definition-permissions-on-a-database"></a>データベースに対する定義の読み取り権限の設定  
 データベース メタデータを読み取る権限を付与すると、データベース内のすべてのオブジェクトのメタデータを読み取るための権限も付与されます。  
  
 `Read Definition`専用の処理のためにロールを設定するときは常に、データベースレベルで権限を含めることをお勧めします。 では、 `Read Definition` 管理者以外のユーザーがでモデルのオブジェクト階層を表示 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] し、後続の処理のために個々のオブジェクトに移動できます。  
  
1.  で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のインスタンスに接続し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、オブジェクトエクスプローラーで適切なデータベースの [**ロール**] を展開します。次に、データベースロールをクリックするか、新しいデータベースロールを作成します。  
  
2.  [**全般**] タブで、オプションを選択し `Read Definition` ます。  
  
3.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
4.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>個々のオブジェクトに対する定義の読み取り権限の設定  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、 **[データベース]** フォルダーを開き、データベースを選択します。オブジェクト エクスプローラーでそのデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、または新しいデータベース ロールを作成します。  
  
2.  **[全般**] ペインで、のデータベース権限を消去し `Read Definition` ます。 この手順によって、権限継承が削除され、個々のオブジェクトに対する権限を設定できるようになります。  
  
3.  プロパティを指定するオブジェクトを選択し `Read Definition` ます。  
  
    -   [**データソース**] ペインで、 `Read Definition` そのデータソースのチェックボックスをオンにします。 ロール メンバーは、サーバー名や場合によってはユーザー名も含め、データ ソースの接続文字列を表示できます。 接続文字列を変更する権限やその他のオブジェクトの定義を表示する権限は付与しないで、接続文字列情報を提供する場合に、この権限が使用できます。  
  
    -   [**ディメンション**] ペインで、 `Read Definition` そのディメンションのチェックボックスをオンにします。 熟練したアナリストおよび開発者が、変更権限のない定義を表示したり、他のオブジェクト (他のディメンション、キューブ オブジェクト、マイニング構造、マイニング モデルなど) の定義を表示したりすることが必要になる場合があります。  
  
    -   [マイニング構造] ペインで、 `Read Definition` データマイニング構造またはデータマイニングモデルのチェックボックスをオンにします。 `Read Definition`データモデルを参照するには、が必要です。 詳細については、「[データ マイニング構造およびデータ マイニング モデルに対する権限の付与 &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)」を参照してください。  
  
4.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services &#40;データベースのアクセス許可を付与&#41;](grant-database-permissions-analysis-services.md)   
 [処理権限の付与 &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  
