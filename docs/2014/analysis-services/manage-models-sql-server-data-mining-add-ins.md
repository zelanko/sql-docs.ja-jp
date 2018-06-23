---
title: モデル (SQL Server データ マイニング アドイン) の管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 824c9fb75de1c0d2fcfc7da7cbd3ffcf17c8e38f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084432"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a>モデルの管理 (SQL Server データ マイニング アドイン)
  ![管理モデル ボタン、データ マイニング リボン](media/dmc-manage.gif "モデルの管理 ボタン、データ マイニング リボン")  
  
 **モデルの管理** ダイアログ ボックスでは、既存のマイニング モデルおよびマイニング構造に格納されていると対話することができます、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は現在接続されているサーバー。 さらに、現在のセッション中に作成された一時的な構造およびモデルを表示および管理できます。 セッション モデルおよびサーバー上に格納されているモデルをこれまでに使用している場合、ダイアログ ボックスにこれらのモデルが表示されます。  
  
## <a name="using-the-manage-models-wizard"></a>モデルの管理ウィザードの使用  
 クリックすると、**モデルの管理**、 **[マイニング構造およびモデル**] ダイアログ ボックスが開き、既存のデータ マイニング モデルおよび構造を管理するため、次の機能へのアクセスを提供します。  
  
-   マイニング モデルまたは構造の名前を変更する。  
  
-   マイニング モデルまたは構造を削除する。  
  
-   マイニング モデルまたは構造を消去する。  
  
-   新しいデータまたは既存のデータを使用してマイニング構造を処理する。  
  
-   マイニング モデルまたは構造をエクスポートまたはインポートする。  
  
> [!NOTE]  
>  このダイアログ ボックスを使用してクエリまたはモデルを作成することはできません。 新しいマイニング構造を作成するには、使用すると、Excel 用データ マイニング クライアントで提供されるウィザードの 1 つを使用、**データ マイニング詳細クエリ エディター**です。  
  
### <a name="requirements"></a>要件  
 データ マイニング モデルを管理するには、最初に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を作成する必要があります。 一時ファイルに保存されているセッション モデルを操作する場合も同様です。 作成または接続を変更する方法の詳細については、次を参照してください。[ソース データへの接続&#40;Excel 用データ マイニング クライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)です。  
  
 接続先の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに既存のデータ マイニング構造またはデータ マイニング モデルがない場合は、ウィザードまたはこのアドインに用意されているその他のツールを使用して、データ マイニング構造またはデータ マイニング モデルを作成できます。 使用して、新しいモデルを作成することも、**データ マイニング モデルの詳細エディター**です。  
  
## <a name="see-also"></a>参照  
 [マイニング モデルを文書化&#40;アドイン Excel 用データ マイニング&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)   
 [展開して、マイニング モデルをスケーリング&#40;アドイン Excel 用データ マイニング&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  