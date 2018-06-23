---
title: Grant 定義の読み取りアクセス許可オブジェクトのメタデータ (Analysis Services) |Microsoft ドキュメント
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
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a0a7a6459b282d94801d277bc160b28f15840c59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085112"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>オブジェクト メタデータに対する定義の読み取り権限の付与 (Analysis Services)
  管理者は、選択したオブジェクトのオブジェクト定義またはメタデータを読み取る権限を使用して、オブジェクトの定義の変更、オブジェクトの構造の変更、またはオブジェクトの実際のデータの表示を行う権限を付与することなく、オブジェクト情報を表示する権限を付与できます。 `Read Definition` データベース、データ ソース、ディメンション、マイニング構造およびマイニング モデルのレベルでは、アクセス許可を付与できます。 必要な場合`Read Definition`有効にする必要があります、キューブのアクセス許可、`Read Definition`データベース用です。権限は加算します。 たとえば、あるロールではキューブのメタデータを読み取るための権限を付与し、別のロールでは同じユーザーにディメンションのメタデータを読み取るための権限を付与します。 これら 2 つの異なるロールの権限は組み合わされ、キューブのメタデータを読み取る権限と、そのデータベース内のディメンションのメタデータを読み取る権限をユーザーに与えることになります。  
  
> [!NOTE]  
>  データベースのメタデータを読み取る権限は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]データベースに接続するために必要な最小限の権限です。 また、メタデータを読み取る権限を持つユーザーは、DISCOVER_XML_METADATA スキーマ行セットを使用して、オブジェクトのクエリを行い、そのメタデータを表示できます。 詳細については、「 [DISCOVER_XML_METADATA 行セット](../schema-rowsets/xml/discover-xml-metadata-rowset.md)」を参照してください。  
  
## <a name="set-read-definition-permissions-on-a-database"></a>データベースに対する定義の読み取り権限の設定  
 データベース メタデータを読み取る権限を付与すると、データベース内のすべてのオブジェクトのメタデータを読み取るための権限も付与されます。  
  
 含めることをお勧め、`Read Definition`専用処理のためのロールを設定しているときに、データベース レベルでアクセスを許可します。 持つ`Read Definition`管理者以外のユーザーにモデルのオブジェクト階層を表示するのには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]後続の処理の個々 のオブジェクトに移動します。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーで適切なデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、新しいデータベース ロールを作成します。  
  
2.  **全般**] タブで、[、`Read Definition`オプション。  
  
3.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
4.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>個々のオブジェクトに対する定義の読み取り権限の設定  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、 **[データベース]** フォルダーを開き、データベースを選択します。オブジェクト エクスプローラーでそのデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、または新しいデータベース ロールを作成します。  
  
2.  **全般** ウィンドウでのデータベース アクセス許可をオフ`Read Definition`です。 この手順によって、権限継承が削除され、個々のオブジェクトに対する権限を設定できるようになります。  
  
3.  指定したオブジェクトを選択して`Read Definition`プロパティ。  
  
    -   **データ ソース** ウィンドウで、をクリックして、`Read Definition`そのデータ ソースのチェック ボックスです。 ロール メンバーは、サーバー名や場合によってはユーザー名も含め、データ ソースの接続文字列を表示できます。 接続文字列を変更する権限やその他のオブジェクトの定義を表示する権限は付与しないで、接続文字列情報を提供する場合に、この権限が使用できます。  
  
    -   **ディメンション** ウィンドウで、をクリックして、`Read Definition`そのディメンションのチェック ボックスです。 熟練したアナリストおよび開発者が、変更権限のない定義を表示したり、他のオブジェクト (他のディメンション、キューブ オブジェクト、マイニング構造、マイニング モデルなど) の定義を表示したりすることが必要になる場合があります。  
  
    -   マイニング構造 ペインでをクリックして、`Read Definition`データ マイニング構造またはモデルのチェック ボックスです。 `Read Definition` データ モデルを参照する必要があります。 詳細については、「[データ マイニング構造およびデータ マイニング モデルに対する権限の付与 &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)」を参照してください。  
  
4.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
5.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="see-also"></a>参照  
 [データベースのアクセス許可を付与&#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [プロセスのアクセス許可を与える&#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  