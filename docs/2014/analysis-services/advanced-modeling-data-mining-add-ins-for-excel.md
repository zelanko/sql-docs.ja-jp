---
title: 高度なモデリング (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6de68fe97c61d90372f77f0fa318221f8f6e3ba7
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528242"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a>高度なモデリング (Excel 用データ マイニング アドイン)
  **高度な**データモデリングオプションを使用すると、ウィザードによって作成されたものとは異なるパラメーターを使用して、カスタムデータマイニング構造およびモデルを作成できます。 このセクションで説明する 2 つのウィザードでは、まったく新しいデータ マイニング構造を作成したり、既存のデータ マイニング構造に適用する新しいマイニング モデルを作成したりできます。  
  
## <a name="create-mining-structure"></a>マイニング構造の作成  
 ![[データ マイニング] リボンの [マイニング構造の作成] ボタン](media/dmc-createstruct.gif "[データ マイニング] リボンの [マイニング構造の作成] ボタン")  
  
 **マイニング構造の作成ウィザード**を使用すると、新しいデータマイニング構造を構築できます。 構造とは、指定したデータ ソースから抽出したデータのコレクションです。  マイニング構造は、基になる新しいデータで更新できますが、マイニング構造を作成するときは、分析時のデータの使用方法を定義するデータ型と名前を定義します。  
  
 Excel テーブル、Excel 範囲、または [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソース ビューとして定義済みである外部データ ソースの任意のデータをデータ ソースとして、構造を構築することができます。  
  
 テスト用および検証用のデータを構造ごとに確保することができます。 データソースを設定するときに、この*予約データセット*を作成することによって、構造に基づくすべてのモデルで、テストに一貫性のあるデータセットを使用できるようになります。  
  
 マイニング構造を作成した後、複数のモデルを追加して、異なる分析方法を適用することができます。  
  
 **マイニング構造の作成ウィザード**を使用する方法の詳細については、「 [create マイニング Structure &#40;SQL Server データマイニングアドイン&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)」を参照してください。  
  
## <a name="add-model-to-structure"></a>構造へのモデルの追加  
 ![[構造へのモデルの追加] ボタン](media/dmc-addmodel.gif "[構造へのモデルの追加] ボタン")  
  
 新しいモデルを構造に追加する場合は、別のアルゴリズムまたは別のパラメーターを使用してデータを分析します。 このオプションは、データ マイニング クライアント ツールで公開されていないアルゴリズムの 1 つを使用してモデルを作成する場合に特に役立ちます。  
  
 たとえば、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でサポートされている次のようなアルゴリズムを使用することができます。  
  
-   Linear regression (線形回帰)  
  
-   シーケンス クラスター  
  
-   入れ子になったデータ セットのアソシエーション分析  
  
 使用できるマイニング構造の種類を確認するには、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **モデルの管理**] または [**参照**] をクリックして、に格納されているモデルと構造を参照できます。  
  
 使用できるのは、現在のセッション中に作成されたデータ マイニング構造、または、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに保存されたマイニング構造に限定されています。  
  
 詳細については、「 [Add Model To Structure &#40;&#41;Excel 用データマイニングアドイン](add-model-to-structure-data-mining-add-ins-for-excel.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データマイニングアドイン SQL Server &#40;モデルの管理&#41;](manage-models-sql-server-data-mining-add-ins.md)   
 [Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
