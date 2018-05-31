---
title: Microsoft SQL データベースでのインテリジェントなクエリ処理 | Microsoft Docs
description: SQL Server および Azure SQL Database のクエリ パフォーマンスを向上させるためのインテリジェントなクエリ処理の機能です。
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7786fd048f1698c90f379450b31e0bac3457706e
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455768"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>SQL データベースでのインテリジェントなクエリ処理
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

**インテリジェントなクエリ処理**機能ファミリには、実装の労力は最小限で既存のワークロードのパフォーマンスを改善する、広範な影響がある機能が含まれています。   これには、既存のコンストラクトの改善や、アダプティブな方法と機能の導入も含まれています。  

## <a name="adaptive-query-processing"></a>アダプティブ クエリ処理
インテリジェントなクエリ処理での機能ファミリは、SQL Server 2017 および Azure SQL Database で導入されたアダプティブ クエリ処理の機能ファミリであり、これによってアプリケーションのワークロードのランタイム条件に最適化戦略を適用する、新しいクエリ処理機能全体が追加されています。
- **バッチ モードの適応型結合**。 この機能により、キャッシュされている単独プランの実行中に、プランをより優れた結合戦略に動的に切り替えることができます。
- **バッチ モード メモリ許可フィードバック**。 この機能はクエリに必要な実際のメモリを再計算して、キャッシュされているプランで許可されている値を更新するため、同時実行に影響する過大なメモリ許可が少なくなり、過剰なディスク書き込みの原因となる過小評価されたメモリ許可が修正されます。
- **複数ステートメントのテーブル値関数のインターリーブ実行 (MSTVF)**。 インターリーブ実行では、関数に基づく実際の行数を使用して、より正確なダウンストリーム クエリ プランを決定します。 

アダプティブ クエリ処理の詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」を参照してください。

## <a name="see-also"></a>参照
[SQL Server データベース エンジンと Azure SQL Database のパフォーマンス センター](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[クエリ処理アーキテクチャ ガイド](../../relational-databases/query-processing-architecture-guide.md)    
[プラン表示の論理操作と物理操作のリファレンス](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[結合](../../relational-databases/performance/joins.md)    
[アダプティブ クエリ処理のデモンストレーション](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)        
