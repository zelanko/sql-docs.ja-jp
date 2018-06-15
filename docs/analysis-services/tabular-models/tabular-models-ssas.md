---
title: 表形式モデル |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e85a618379b5b3c6da010c8b25782ed6836edb4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040347"
---
# <a name="tabular-models"></a>テーブル モデル
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  表形式モデルは、インメモリ モードまたは DirectQuery モードで実行される Analysis Services データベースで、バックエンド リレーショナル データ ソースから直接取得したデータにアクセスします。 最新の圧縮アルゴリズムおよびマルチ スレッド クエリ プロセッサを使用するは、分析エンジンは、Power BI と Excel などのクライアント アプリケーションを報告することによって、表形式モデル オブジェクトとデータを高速アクセスを提供します。  
  
 DirectQuery は、代替クエリ モードでは、モデルのインメモリ モデルでは、既定値が、大きすぎて、メモリ内、またはデータの揮発性によって妥当な処理方法。 DirectQuery ではさまざまなデータ ソース、DirectQuery モデルでは、バックエンド データベースにアクセスし、クエリを実行する DAX 式を使用して行レベルのセキュリティの計算されるテーブルと列を処理する機能のサポートにより、インメモリ モデルと同等の機能高速なスループットを最適化します。
  
 表形式モデルに作成されますが[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]モデル、テーブル、リレーションシップ、および DAX 式を作成するためのデザイン画面を提供する表形式モデル プロジェクト テンプレートを使用します。 複数のソースからデータをインポートした後、リレーションシップ、計算テーブルおよび列、メジャー、KPI、階層、および翻訳を追加して、モデルを拡充することができます。  
  
 Azure Analysis Services に配置できるモデルまたは表形式サーバー モード用 SQL Server Analysis Services のインスタンスに構成します。 配置済みテーブル モデルは、SQL Server Management Studio で管理できます。 モデルが増すにつれて、処理を最適化するためにパーティション分割し、ロール ベース セキュリティを使用して、行レベルに保護することがことができます。  

  
  
