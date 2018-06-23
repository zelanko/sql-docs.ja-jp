---
title: メモリ最適化テーブルのチェックポイント操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 36c71e149a27443a38781dc9a39592f5c720a3ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177753"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>メモリ最適化テーブルのチェックポイント操作
  データ ファイルとデルタ ファイルのメモリ最適化データに対してチェックポイントを定期的に作成して、トランザクション ログのアクティブな部分を進める必要があります。 チェックポイントにより、メモリ最適化テーブルでは最後に正常終了したチェックポイントまで復元および復旧することができ、トランザクション ログのアクティブな部分が適用されてメモリ最適化テーブルが更新され、復旧が完了します。 ディスク ベース テーブルとメモリ最適化テーブルのチェックポイント操作は個別の操作です。 ディスク ベース テーブルとメモリ最適化テーブルに関する各シナリオとチェックポイント動作について、次に説明します。  
  
## <a name="manual-checkpoint"></a>手動チェックポイント  
 手動でチェックポイントを作成すると、ディスク ベース テーブルおよびメモリ最適化テーブルの両方のチェックポイントが閉じられます。 アクティブなデータ ファイルは、一部分しか入力されていない場合でも閉じられます。  
  
## <a name="automatic-checkpoint"></a>自動チェックポイント  
 自動チェックポイントは、ディスク ベース テーブルとメモリ最適化テーブルではデータの保存方法が異なるため、実装方法が異なります。  
  
 ディスクベースのテーブルの場合、recovery interval 構成オプションに基づいて自動チェックポイントが取得されます (詳細については、「[データベースのターゲットの復旧時間の変更 &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md)」を参照してください)。  
  
 メモリ最適化テーブルでは、自動チェックポイントは最後のチェックポイント以降のトランザクション ログ ファイルが 512 MB よりも大きくになったときに取得します。 512 MB には、両方ディスク ベース テーブルとメモリ最適化テーブルのトランザクション ログ レコードが含まれています。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化オブジェクト用ストレージの作成と管理](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  