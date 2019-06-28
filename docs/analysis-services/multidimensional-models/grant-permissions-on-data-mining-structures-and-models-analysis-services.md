---
title: データ マイニング構造およびモデル (Analysis Services) に対するアクセス許可を付与 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91e805488ff5a90b4f358cb908fe2efa6fd8d04a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023059"
---
# <a name="grant-permissions-on-data-mining-structures-and-models-analysis-services"></a>データ マイニング構造およびデータ マイニング モデルに対する権限の付与 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  既定では、Analysis Services サーバー管理者にのみ、データベースのデータ マイニング構造またはマイニング モデルを表示する権限があります。 管理者以外のユーザーに権限を付与するには、次の手順に従ってください。  
  
## <a name="set-permissions-to-access-a-mining-structure"></a>マイニング構造にアクセスするための権限の設定  
  
1.  SSMS で、Analysis Services に接続します。 手順について不明な点がある場合は、「[クライアント アプリケーションからの接続 &#40;Analysis Services&#41;](../../analysis-services/instances/connect-from-client-applications-analysis-services.md)」を参照してください。  
  
2.  オブジェクト エクスプローラーで **[データベース]** フォルダーを開き、データベースを選択します。  
  
3.  **[ロール]** を右クリックし、 **[新しいロール]** を選択します。  
  
4.  [全般] ページで、名前を入力し、必要に応じて説明を入力します。 このページには、フル コントロール、データベースの処理、定義の読み取りなどデータベース権限もいくつか含まれています。 これらのいずれの権限も、データ マイニングのアクセスには必要ありません。 データべース権限の詳細については、「[データベース権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)」を参照してください。  
  
5.  **[マイニング構造]** ペインで、データ マイニング構造ごとに **[読み取り]** または **[読み取り/書き込み]** を選択します。  
  
6.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
7.  **[OK]** をクリックして、ロールの作成を終了します。  
  
## <a name="set-permissions-to-access-a-mining-model"></a>マイニング モデルにアクセスするための権限の設定  
 データ マイニング モデルの場合、ロールに **[読み取り]** 権限または **[読み取り/書き込み]** 権限を設定できるほか、 **[ドリルスルー]** 権限および **[定義の読み取り]** 権限を設定して基になるデータの表示および参照を許可することもできます。  
  
 **注** マイニング構造とマイニング モデルの両方についてドリルスルーを有効にした場合、そのマイニング モデルとマイニング構造に対するドリルスルー権限を持つロールのすべてのメンバー ユーザーが、マイニング構造内の列を表示できるようになります。これらの列がマイニング モデルに含まれていなかったとしても同様です。 したがって、機密情報を保護するため、個人情報をマスクするデータ ソース ビューを設定し、マイニング構造に対するドリルスルー アクセスは必要な場合にのみ許可する必要があります。  
  
 データベース ロールに読み取り権限または読み取り/書き込み権限を与えるには、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー ロールのメンバーであるか、フル コントロール (管理者) 権限を持つ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース ロールのメンバーである必要があります。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーで適切なデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、新しいデータベース ロールを作成します。  
  
2.  **[マイニング構造]** ペインで、 **[マイニング モデル]** ボックスの一覧からマイニング モデルを見つけ、そのマイニング モデルの **[読み取り]**、 **[読み取り/書き込み]**、 **[ドリルスルー]**、または **[参照]** を選択します。  
  
3.  **[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。  
  
4.  **[OK]** をクリックして、ロールの作成を終了します。  
  
 データ マイニング拡張機能 (DMX) の OPENQUERY 句を使用するドリルスルー クエリでデータ ソースを使用するには、適切なデータ ソース オブジェクトに対する読み取り/書き込み権限もデータベース ロールに与える必要があります。 詳細については、「[データ ソース オブジェクトに対する権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md)」および[OPENQUERY &#40;DMX&#41;](../../dmx/source-data-query-openquery.md)」を参照してください。  
  
> [!NOTE]  
>  既定では、OPENROWSET を使った DMX クエリの送信が無効になっています。  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスにサーバー管理者権限を付与する](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [キューブまたはモデル権限 & #40; を許可します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)   
 [データ & #40; をディメンションにカスタムのアクセスを許可します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)   
 [セルのデータ & #40; へのカスタム アクセスを許可します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
  
