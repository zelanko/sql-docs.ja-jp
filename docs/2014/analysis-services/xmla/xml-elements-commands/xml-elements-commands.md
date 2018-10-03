---
title: コマンド (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e5e51d1989b3c492814f5958bacd82bbc01ef76d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105382"
---
# <a name="commands-xmla"></a>コマンド (XMLA)
  このリファレンス セクションでは、`Command` メソッドの呼び出し時に `Execute` 要素の中で使用できる XML for Analysis (XMLA) 要素について説明します。  
  
|要素|説明|  
|-------------|-----------------|  
|[Alter 要素 (XMLA)](alter-element-xmla.md)|使用される Analysis Services スクリプト言語 (ASSL) 要素を含む、 [Execute](../xml-elements-methods-execute.md)メソッドのインスタンス上のオブジェクトを変更する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。|  
|[Backup 要素](backup-element-xmla.md)|バックアップ、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースをバックアップ ファイルにします。|  
|[Batch 要素](batch-element-xmla.md)|実行します 1 つまたは複数の XML for Analysis (XMLA) コマンド、バッチ操作として順次またはのインスタンスに同時に[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。|  
|[BeginTransaction 要素](begintransaction-element-xmla.md)|Analysis Services インスタンスに対する現在のセッションで、トランザクションを開始します。|  
|[Cancel 要素](cancel-element-xmla.md)|Analysis Services インスタンス上で現在実行中のコマンドを取り消します。|  
|[ClearCache 要素](clearcache-element-xmla.md)|Analysis Services インスタンス上の指定されたオブジェクトのメモリ キャッシュを消去します。|  
|[CommitTransaction 要素](committransaction-element-xmla.md)|Analysis Services インスタンスに対する現在のセッションで、トランザクションをコミットします。|  
|[Create 要素](create-element-xmla.md)|使用される Analysis Services スクリプト言語 (ASSL) 要素を含む、 [Execute](../xml-elements-methods-execute.md) Analysis Services インスタンス上のオブジェクトを作成するメソッド。|  
|[Delete 要素](delete-element-xmla.md)|Analysis Services インスタンス上のオブジェクトを削除します。|  
|[DesignAggregations 要素](designaggregations-element-xmla.md)|Analysis Services インスタンスには、集計デザイン用の集計を作成します。|  
|[Drop 要素](drop-element-xmla.md)|属性メンバーをディメンションから削除します。|  
|[Insert 要素](insert-element-xmla.md)|属性メンバーをディメンションに挿入します。|  
|[Lock 要素](lock-element-xmla.md)|Analysis Services インスタンス上の指定されたオブジェクトをロックします。|  
|[MergePartitions 要素](mergepartitions-element-xmla.md)|対象パーティションに 1 つまたは複数のソース パーティションのデータをマージし、し、基になるパーティションを削除します。|  
|[NotifyTableChange 要素](notifytablechange-element-xmla.md)|指定されたデータ ソース内のテーブルの内容が変更されたことを Analysis Services インスタンスに通知します。|  
|[Process 要素](process-element-xmla.md)|Analysis Services インスタンス上のオブジェクトを処理します。|  
|[Restore 要素](restore-element-xmla.md)|Analysis Services データベースをバックアップ ファイルから復元します。|  
|[RollbackTransaction 要素](rollbacktransaction-element-xmla.md)|Analysis Services インスタンスに対する現在のセッションで、トランザクションをロールバックします。|  
|[Statement 要素](statement-element-xmla.md)|格納クエリまたは送信されるステートメントを使用して、 [Execute](../xml-elements-methods-execute.md) Analysis Services のインスタンスにメソッド。|  
|[Subscribe 要素](subscribe-element-xmla.md)|トレースをサブスクライブして、トレース イベントを含む行セットを Analysis Services インスタンスから返します。|  
|[Synchronize 要素](synchronize-element-xmla.md)|Analysis Services データベースを既存の別のデータベースと同期させます。|  
|[Unlock 要素](unlock-element-xmla.md)|Analysis Services インスタンス上の指定されたロックを解除します。|  
|[Update 要素](../xml-elements-commands/update-element-xmla.md)|ディメンション内の属性メンバーを更新します。|  
|[UpdateCells 要素](updatecells-element-xmla.md)|書き込み許可キューブ内のセルを更新します。|  
  
  
