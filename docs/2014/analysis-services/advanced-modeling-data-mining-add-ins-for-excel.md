---
title: 高度なモデリング (アドイン Excel 用データ マイニング) |Microsoft ドキュメント
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
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: de7eea9099b458a9f16e6928c1535dc4a03eb81a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073874"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a>高度なモデリング (Excel 用データ マイニング アドイン)
  使用することができます、**詳細**データ モデリングを作成するカスタム データ マイニング構造とモデル パラメーターを使用して、ウィザードによって作成されたものとは異なるオプションです。 このセクションで説明する 2 つのウィザードでは、まったく新しいデータ マイニング構造を作成したり、既存のデータ マイニング構造に適用する新しいマイニング モデルを作成したりできます。  
  
## <a name="create-mining-structure"></a>マイニング構造を作成します。  
 ![マイニング構造の作成 ボタン、データ マイニング リボン](media/dmc-createstruct.gif "Create Mining Structure ボタン、データ マイニング リボン")  
  
 **マイニング構造の作成ウィザード**新しいデータ マイニング構造を構築できます。 構造とは、指定したデータ ソースから抽出したデータのコレクションです。  マイニング構造は、基になる新しいデータで更新できますが、マイニング構造を作成するときは、分析時のデータの使用方法を定義するデータ型と名前を定義します。  
  
 Excel テーブル、Excel 範囲、または [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソース ビューとして定義済みである外部データ ソースの任意のデータをデータ ソースとして、構造を構築することができます。  
  
 テスト用および検証用のデータを構造ごとに確保することができます。 これを作成することで*予約データ セット*データ ソースを設定するときは、構造に基づくすべてのモデルがテストに一貫したデータ セットを使用することができることを確認することができます。  
  
 マイニング構造を作成した後、複数のモデルを追加して、異なる分析方法を適用することができます。  
  
 使用する方法についての詳細、**マイニング構造の作成ウィザード**を参照してください[Create Mining Structure &#40;SQL Server データ マイニング アドイン&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)です。  
  
## <a name="add-model-to-structure"></a>構造へのモデルの追加  
 ![モデル構造 ボタンを追加](media/dmc-addmodel.gif "構造ボタンにモデルの追加")  
  
 新しいモデルを構造に追加する場合は、別のアルゴリズムまたは別のパラメーターを使用してデータを分析します。 このオプションは、データ マイニング クライアント ツールで公開されていないアルゴリズムの 1 つを使用してモデルを作成する場合に特に役立ちます。  
  
 たとえば、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でサポートされている次のようなアルゴリズムを使用することができます。  
  
-   線形回帰  
  
-   シーケンス クラスター  
  
-   入れ子になったデータ セットのアソシエーション分析  
  
 マイニング構造の種類を確認するのに使用可能なすることができますモデルおよび参照に格納されている構造体[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]をクリックして**モデルの管理**または**参照**です。  
  
 使用できるのは、現在のセッション中に作成されたデータ マイニング構造、または、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに保存されたマイニング構造に限定されています。  
  
 詳細については、次を参照してください。[構造へのモデルの追加&#40;Excel 用データ マイニング アドイン&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)です。  
  
## <a name="see-also"></a>参照  
 [モデルの管理&#40;SQL Server データ マイニング アドイン&#41;](manage-models-sql-server-data-mining-add-ins.md)   
 [Excel におけるモデルの参照&#40;SQL Server データ マイニング アドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  