---
title: 表形式モデル |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/30/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2886f357fc93b1ae39197c7624cac88b2bc18837
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tabular-models"></a>テーブル モデル
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  表形式モデルは、インメモリ モードまたは DirectQuery モードで実行される Analysis Services データベースで、バックエンド リレーショナル データ ソースから直接取得したデータにアクセスします。 最新の圧縮アルゴリズムおよびマルチ スレッド クエリ プロセッサを使用するは、分析エンジンは、Power BI と Excel などのクライアント アプリケーションを報告することによって、表形式モデル オブジェクトとデータを高速アクセスを提供します。  
  
 DirectQuery は、代替クエリ モードでは、モデルのインメモリ モデルでは、既定値が、大きすぎて、メモリ内、またはデータの揮発性によって妥当な処理方法。 DirectQuery ではさまざまなデータ ソース、DirectQuery モデルでは、バックエンド データベースにアクセスし、クエリを実行する DAX 式を使用して行レベルのセキュリティの計算されるテーブルと列を処理する機能のサポートにより、インメモリ モデルと同等の機能高速なスループットを最適化します。
  
 表形式モデルに作成されますが[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]モデル、テーブル、リレーションシップ、および DAX 式を作成するためのデザイン画面を提供する表形式モデル プロジェクト テンプレートを使用します。 複数のソースからデータをインポートした後、リレーションシップ、計算テーブルおよび列、メジャー、KPI、階層、および翻訳を追加して、モデルを拡充することができます。  
  
 Azure Analysis Services に配置できるモデルまたは表形式サーバー モード用 SQL Server Analysis Services のインスタンスに構成します。 配置済みテーブル モデルは、SQL Server Management Studio で管理できます。 モデルが増すにつれて、処理を最適化するためにパーティション分割し、ロール ベース セキュリティを使用して、行レベルに保護することがことができます。  

  
  
