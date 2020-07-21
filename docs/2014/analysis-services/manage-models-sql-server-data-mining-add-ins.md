---
title: モデルの管理 (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
author: minewiskan
ms.author: owend
ms.openlocfilehash: f37939fea1188c18079fc7e619cee6a336876e24
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541854"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a>モデルの管理 (SQL Server データ マイニング アドイン)
  ![[データ マイニング] リボンの [モデルの管理] ボタン](media/dmc-manage.gif "[データ マイニング] リボンの [モデルの管理] ボタン")  
  
 [**モデルの管理**] ダイアログボックスを使用すると、現在接続しているサーバーに格納されている既存のマイニングモデルとマイニング構造を操作でき [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。 さらに、現在のセッション中に作成された一時的な構造およびモデルを表示および管理できます。 セッション モデルおよびサーバー上に格納されているモデルをこれまでに使用している場合、ダイアログ ボックスにこれらのモデルが表示されます。  
  
## <a name="using-the-manage-models-wizard"></a>モデルの管理ウィザードの使用  
 [モデルの**管理**] をクリックすると、[**マイニング構造とマイニングモデルの管理**] ダイアログボックスが開き、既存のデータマイニングモデルおよび構造を管理するための次の機能にアクセスできます。  
  
-   マイニング モデルまたは構造の名前を変更する。  
  
-   マイニング モデルまたは構造を削除する。  
  
-   マイニング モデルまたは構造を消去する。  
  
-   新しいデータまたは既存のデータを使用してマイニング構造を処理する。  
  
-   マイニング モデルまたは構造をエクスポートまたはインポートする。  
  
> [!NOTE]  
>  このダイアログ ボックスを使用してクエリまたはモデルを作成することはできません。 新しいマイニング構造を作成するには、Excel 用のデータマイニングクライアントに用意されているウィザードのいずれかを使用するか、**詳細エディターデータマイニングクエリ**を使用します。  
  
### <a name="requirements"></a>要件  
 データ マイニング モデルを管理するには、最初に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を作成する必要があります。 一時ファイルに保存されているセッション モデルを操作する場合も同様です。 接続を作成または変更する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。  
  
 接続先の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに既存のデータ マイニング構造またはデータ マイニング モデルがない場合は、ウィザードまたはこのアドインに用意されているその他のツールを使用して、データ マイニング構造またはデータ マイニング モデルを作成できます。 **詳細エディターのデータマイニングモデル**を使用して新しいモデルを作成することもできます。  
  
## <a name="see-also"></a>参照  
 [Excel 用データマイニングアドイン &#40;マイニングモデルのドキュメント化&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)   
 [Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
