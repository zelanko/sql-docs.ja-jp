---
title: "プロアクティブ キャッシュ (ディメンション) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5df335ed29cb7e899347b189d3c48183f1d5b020
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="proactive-caching-dimensions"></a>プロアクティブ キャッシュ (ディメンション)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]プロアクティブ キャッシュは、自動 MOLAP キャッシュの作成と管理の OLAP オブジェクトを提供します。 データベース内のデータに加えられた変更は、データベースからの通知に基づき、すぐにキューブに反映されます。 プロアクティブ キャッシュの目標は、従来の MOLAP のパフォーマンスを提供しながら、ROLAP の即時性と管理のしやすさを保つことです。  
  
 簡単な <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトは、タイミングの指定およびテーブル通知で構成されます。 タイミングの指定は、変更通知を受信してからキャッシュが更新されるまでのタイムフレームを定義します。 テーブル通知は、データ テーブルと <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトとの間の通知スキーマを定義します。  
  
  
