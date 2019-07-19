---
title: Analysis Services における表形式モデル |Microsoft Docs
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae7dfd78e71c41ab5b826a27742923445117417d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162437"
---
# <a name="tabular-models"></a>テーブル モデル
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Analysis Services における表形式モデルには、メモリ内またはバックエンドのリレーショナル データから直接ソース データに接続して、DirectQuery モードで実行しているデータベースです。 最新の圧縮アルゴリズムおよびマルチ スレッド クエリ プロセッサを使用して、Analysis Services Vertipaq の分析エンジンが Power BI や Excel などのクライアント アプリケーションを報告することによって表形式モデル オブジェクトおよびデータに高速アクセスを提供します。  
  
 DirectQuery は、代替クエリ モードでは、モデル、インメモリ モデルでは、既定値が、大きすぎて、メモリ内、またはデータの揮発性のため、適切な処理の方法に収まりません。 DirectQuery の幅広いデータ ソース、計算テーブルおよび DirectQuery モデルではバックエンド データベースにアクセスし、クエリを実行する DAX 式を使用して行レベルのセキュリティ列を処理する機能のサポートにより、インメモリ モデルと同等を実現します。高速なスループットを最適化します。
  
 表形式モデルで作成[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]表形式モデル プロジェクト テンプレートを使用します。 プロジェクト テンプレートは、テーブル、パーティション、リレーションシップ、階層、メジャー、Kpi などのセマンティック モデル オブジェクトを作成するためのデザイン サーフェイスを提供します。 
  
 表形式モデルは、Azure Analysis Services または表形式サーバー モード用に構成された SQL Server Analysis Services のインスタンスに配置することができます。 配置済みテーブル モデルは、SQL Server Management Studio で管理できます。 

ここに含まれる表形式モデルのドキュメントは、ほとんどの場合、SQL Server Analysis Services と Azure Analysis Services の両方に適用されます。 Azure Analysis Services に固有の記事は、他の Azure ドキュメントと共に公開されます。 詳細についてを参照してください。 [Azure Analysis Services のドキュメント](https://docs.microsoft.com/azure/analysis-services/)します。
  
