---
title: モデルの検証と予測用のモデルの使用 (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97268dac1fef029bc35ff702ace0d422ee296d65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66065498"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a>モデルの検証と予測用モデルの使用 (Excel 用データ マイニング アドイン)
  モデルのテストと検証は、データ マイニング プロセスにおける重要な手順です。 実際のデータに対するマイニング モデルの性能を、運用環境に配置する前に知っておく必要があります。  
  
 データ マイニング アドインには、構築したモデルをテストし、そのモデルを使用して予測と提案を作成するためのツールが含まれています。  
  
## <a name="accuracy-chart"></a>精度チャート  
 **精度チャート**ウィザードを使用すると、予測クエリを作成し、リフトチャートまたは散布図を作成することによって、データマイニングモデルのパフォーマンスを評価できます。 ほぼ同じ構造を持つ 2 つのモデルを区別し、どちらの予測精度が高いかを調べるにはリフト チャートが有効です。  
  
 [精度チャート &#40;SQL Server データマイニングアドイン&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a>分類マトリックス  
 **分類マトリックス**ウィザードを使用すると、予測クエリを作成して分類モデルのパフォーマンスを評価できます。 モデルによって生成された正確な予測と不正確な予測を両方示す概要グラフが出力されます。 分類マトリックスは、モデルによって値が正しく予測された頻度だけでなく、モデルによって最も頻繁に誤って予測された値も示されるので、非常に便利なツールです。  
  
 [分類マトリックス &#40;SQL Server データマイニングアドイン&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a>利益チャート  
 **利益チャート**ウィザードを使用すると、データマイニングモデルを使用する利点を比較し、誤検知と誤否定の両方のコストを評価することができます。  
  
 この種類のチャートでは、モデルの予測精度が測定され、単位あたりのコストと全体のコストが組み込まれます。  
  
 [利益チャート &#40;データマイニングアドイン&#41;SQL Server](profit-chart-sql-server-data-mining-add-ins.md)ます。  
  
## <a name="cross-validation"></a>クロス検証  
 クロス検証は、データ セットの妥当性を評価しデータ セットに対するマイニング モデルの精度を評価するための、データ マイニング コミュニティで確立された方法です。 クロス検証では、データ セットをサブセットに分割し、モデルの作成、トレーニング、およびテストを各サブセットに対して繰り返し実行します。  
  
 **クロス検証**ウィザードでは、でデータを分割するフォールドの数を指定できます。また、クロス検証レポートを使用して、これらのセクション間の違いを統計的に説明します。 これに基づいて、モデルが、すべてのトレーニング データに対して適切に機能しているか、特定のサブセットに偏っているかを判断できます。  
  
 [相互検証 &#40;SQL Server データマイニングアドイン&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a>クエリ ウィザード  
 **クエリ**ウィザードは、予測クエリの作成に役立つ対話型のツールです。 クエリによって、提案や将来の予測などを生成する方法が定義されます。  
  
 **クエリ**ウィザードでは、モデルを選択し、単一の値またはテーブルまたは範囲の入力データを指定します。このウィザードを使用して、出力する列を選択できます。 また、確率スコアやその他の有用な統計情報を生成する関数をクエリに追加することもできます。  
  
 [クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a>詳細クエリ エディター  
 **詳細クエリエディター**は、ダイアログボックスの対話型セットであり、カスタムクエリの実行から、新しいモデルの作成とトレーニング、モデルの削除、新しいデータセットの作成まで、あらゆる種類の DMX ステートメントを作成するのに役立ちます。  
  
 [詳細データ マイニング クエリ エディター](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a>参照  
 [データの探索とクリーンアップ](exploring-and-cleaning-data.md)   
 [データマイニングモデルの作成](creating-a-data-mining-model.md)   
 [Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
