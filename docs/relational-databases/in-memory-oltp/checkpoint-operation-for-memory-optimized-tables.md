---
title: "メモリ最適化テーブルのチェックポイント操作 | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 06fefee35162b37e0d627afd46feba719d0e4001
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>メモリ最適化テーブルのチェックポイント操作
  データ ファイルとデルタ ファイルのメモリ最適化データに対してチェックポイントを定期的に作成して、トランザクション ログのアクティブな部分を進める必要があります。 チェックポイントにより、メモリ最適化テーブルでは最後に正常終了したチェックポイントまで復元および復旧することができ、トランザクション ログのアクティブな部分が適用されてメモリ最適化テーブルが更新され、復旧が完了します。 ディスク ベース テーブルとメモリ最適化テーブルのチェックポイント操作は個別の操作です。 ディスク ベース テーブルとメモリ最適化テーブルに関する各シナリオとチェックポイント動作について、次に説明します。  
  
## <a name="manual-checkpoint"></a>手動チェックポイント  
 手動でチェックポイントを作成すると、ディスク ベース テーブルおよびメモリ最適化テーブルの両方のチェックポイントが閉じられます。 アクティブなデータ ファイルは、一部分しか入力されていない場合でも閉じられます。  
  
## <a name="automatic-checkpoint"></a>自動チェックポイント  
 自動チェックポイントは、ディスク ベース テーブルとメモリ最適化テーブルではデータの保存方法が異なるため、実装方法が異なります。  
  
 ディスクベースのテーブルの場合、recovery interval 構成オプションに基づいて自動チェックポイントが取得されます (詳細については、「[データベースのターゲットの復旧時間の変更 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)」を参照してください)。  
  
 メモリ最適化テーブルでは、最後のチェックポイント以降にトランザクション ログ ファイルのサイズが 1.5 GB を超えると自動チェックポイントが作成されます。 この 1.5 GB というサイズには、ディスク ベース テーブルとメモリ最適化テーブルの両方に対するトランザクション ログ レコードが含まれています。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化オブジェクト用ストレージの作成と管理](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
