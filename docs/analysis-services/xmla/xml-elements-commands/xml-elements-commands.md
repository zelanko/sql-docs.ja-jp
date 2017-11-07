---
title: "コマンド (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64577ef2799fd56cc4e404a42fc351be8ece6baa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---commands"></a>コマンドの XML 要素
  このリファレンス セクションには、Analysis (XMLA) 要素内で使用できる XML が含まれています、**コマンド**実行中に、 **Execute**メソッドの呼び出しです。  
  
|要素|Description|  
|-------------|-----------------|  
|[Alter 要素 (XMLA)](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)|によって使用される Analysis Services スクリプト言語 (ASSL) 要素が含まれています、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドのインスタンス上のオブジェクトを変更する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。|  
|[Backup 要素](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|バックアップ、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースをバックアップ ファイル。|  
|[バッチ要素](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)|1 つまたは複数の XML for Analysis (XMLA) コマンドとして実行バッチ操作では、順番またはのインスタンスに同時に[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。|  
|[BeginTransaction 要素](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)|Analysis Services インスタンスに対する現在のセッションで、トランザクションを開始します。|  
|[Cancel 要素](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|Analysis Services インスタンス上で現在実行中のコマンドを取り消します。|  
|[ClearCache 要素](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)|Analysis Services インスタンス上の指定されたオブジェクトのメモリ キャッシュを消去します。|  
|[CommitTransaction 要素](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)|Analysis Services インスタンスに対する現在のセッションで、トランザクションをコミットします。|  
|[要素を作成します。](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|によって使用される Analysis Services スクリプト言語 (ASSL) 要素が含まれています、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドを Analysis Services インスタンス上のオブジェクトを作成します。|  
|[Delete 要素](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)|Analysis Services インスタンス上のオブジェクトを削除します。|  
|[DesignAggregations 要素](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)|Analysis Services インスタンス上には、集計デザインの集計を作成します。|  
|[Drop 要素](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|属性メンバーをディメンションから削除します。|  
|[要素を挿入します。](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)|属性メンバーをディメンションに挿入します。|  
|[要素のロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)|Analysis Services インスタンス上の指定されたオブジェクトをロックします。|  
|[MergePartitions 要素](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)|先パーティションに 1 つまたは複数のソース パーティションのデータをマージし、元のパーティションを削除します。|  
|[NotifyTableChange 要素](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)|指定されたデータ ソース内のテーブルの内容が変更されたことを Analysis Services インスタンスに通知します。|  
|[Process 要素](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|Analysis Services インスタンス上のオブジェクトを処理します。|  
|[Restore 要素](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|Analysis Services データベースをバックアップ ファイルから復元します。|  
|[RollbackTransaction 要素](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)|Analysis Services インスタンスに対する現在のセッションで、トランザクションをロールバックします。|  
|[Statement 要素](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|格納クエリまたは送信されるステートメントを使用して、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Analysis Services のインスタンスへのメソッドです。|  
|[Subscribe 要素](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)|トレースをサブスクライブして、トレース イベントを含む行セットを Analysis Services インスタンスから返します。|  
|[Synchronize 要素](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|Analysis Services データベースを既存の別のデータベースと同期させます。|  
|[Unlock 要素](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|Analysis Services インスタンス上の指定されたロックを解除します。|  
|[Update 要素](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|ディメンション内の属性メンバーを更新します。|  
|[UpdateCells 要素](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|書き込み許可キューブ内のセルを更新します。|  
  
  

