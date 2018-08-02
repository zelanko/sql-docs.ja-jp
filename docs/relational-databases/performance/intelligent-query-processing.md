---
title: Microsoft SQL データベースでのインテリジェントなクエリ処理 | Microsoft Docs
description: SQL Server および Azure SQL Database のクエリ パフォーマンスを向上させるためのインテリジェントなクエリ処理の機能です。
ms.custom: ''
ms.date: 07/25/2018
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
ms.openlocfilehash: 6f1b215e95b7cc911cd2815493eabbbd53a47424
ms.sourcegitcommit: a162a8f02d66c13b32d0b6255b0b52fc80e2187e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39250450"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>SQL データベースでのインテリジェントなクエリ処理
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

**インテリジェントなクエリ処理**機能ファミリには、実装の労力は最小限で既存のワークロードのパフォーマンスを改善する、広範な影響がある機能が含まれています。

![インテリジェントなクエリ処理の機能](./media/1_IQPFeatureFamily.png)

## <a name="adaptive-query-processing"></a>アダプティブ クエリ処理
アダプティブ クエリ処理の機能ファミリには、最適化戦略をアプリケーション ワークロードの実行時条件に適用するクエリ処理の改善が含まれます。 含まれる改善は、バッチ モード アダプティブ結合、メモリ許可フィードバック、複数ステートメントのテーブル値関数のインターリーブ実行などです。

### <a name="batch-mode-adaptive-joins"></a>バッチ モード アダプティブ結合
この機能により、キャッシュされている単独プランの実行中に、プランをより優れた結合戦略に動的に切り替えることができます。

### <a name="row-and-batch-mode-memory-grant-feedback"></a>行モードとバッチ モードのメモリ許可フィードバック
この機能はクエリに必要な実際のメモリを再計算して、キャッシュされているプランで許可されている値を更新するため、同時実行に影響する過大なメモリ許可が少なくなり、過剰なディスク書き込みの原因となる過小評価されたメモリ許可が修正されます。

### <a name="interleaved-execution-for-multi-statement-table-valued-functions-mstvfs"></a>複数ステートメントのテーブル値関数 (MSTVF) のインターリーブ実行
インターリーブ実行では、関数に基づく実際の行数を使用して、より正確なダウンストリーム クエリ プランを決定します。 

詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」をご覧ください。

## <a name="table-variable-deferred-compilation"></a>テーブル変数の遅延コンパイル
テーブル変数の遅延コンパイルを使用すると、テーブル変数を参照するクエリのプランの品質および全体的なパフォーマンスが向上します。 最適化と最初のコンパイルの実行中に、この機能は実際テーブル変数の行数に基づくカーディナリティの推定を反映します。  この正確な行数の情報は、ダウンストリーム プラン操作を最適化するために使用されます。

テーブル変数の遅延コンパイルを使用すると、テーブル変数を参照するステートメントのコンパイルは、そのステートメントが最初に実際に実行されるまで遅延されます。 この遅延コンパイルの動作は、一時テーブルの動作と同じです。この変更によって、元の 1 行の推定値ではなく、実際のカーディナリティを使用できるようになります。 Azure SQL Database でテーブル変数の遅延コンパイルのパブリック プレビューを有効にするには、クエリを実行する際に接続されるデータベースのデータベース互換レベル 150 を有効にします。

詳細については、「[テーブル変数の遅延コンパイル](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation )」をご覧ください。

## <a name="approximate-query-processing"></a>概数クエリ処理
概数クエリ処理とは、絶対的な精度よりも応答性が重要となる場合に、大規模なデータ セット全体の集計を提供するために設計された、新しい機能ファミリです。  たとえば、ダッシュボードに表示するために、100 億の行に対する COUNT(DISTINCT()) を計算する場合などです。  この場合、重要なのは絶対的な精度ではなく、応答性です。 新しい集計関数 APPROX_COUNT_DISTINCT は、グループ内の一意の非 null 値の概数を返します。

詳細については、「[APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md)」をご覧ください。

## <a name="see-also"></a>参照
[SQL Server データベース エンジンと Azure SQL Database のパフォーマンス センター](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[クエリ処理アーキテクチャ ガイド](../../relational-databases/query-processing-architecture-guide.md)    
[プラン表示の論理操作と物理操作のリファレンス](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[結合](../../relational-databases/performance/joins.md)    
[アダプティブ クエリ処理のデモンストレーション](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)        
