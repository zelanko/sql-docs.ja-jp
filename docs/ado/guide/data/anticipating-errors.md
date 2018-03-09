---
title: "エラーを予測する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- anticipating errors [ADO]
- errors [ADO], preventing
- preventing errors [ADO]
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3343e525bba78fe0a020208ff35cc620fbf49184
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="anticipating-errors"></a>エラーを予測します。
エラーの防止は、エラー処理と少なくとも同じくらい重要です。 この最後のセクションには、エラーが発生しにくくするために、アプリケーションがかかることが対策の短い一覧が含まれています。  
  
 値を確認してオブジェクトの状態を確認して、**状態**プロパティ オブジェクトを使用して、操作を実行する前にします。 例では、アプリケーションがグローバルで使用する場合の**接続**、確認、**状態**プロパティを呼び出す前に開いているかどうかには既に確認して、**を開く**メソッドです。  
  
-   ユーザーからのデータを受け入れる任意のプログラムは、データ ストアに送信する前にそのデータを検証するコードを含める必要があります。 データ ストア、プロバイダー、ADO、または問題の通知も使用するプログラミング言語に依存することはできません。 データが、そのフィールドの正しい型であること、および必須フィールドが空ではないことを確認して、ユーザーが入力したすべてのバイト数を確認する必要があります。  
  
 データ ストアに、データの書き込みを行う前に、データを確認します。 これを行う最も簡単な方法は処理する、 **WillMove**イベントまたは**WillUpdateRecordset**イベント。 ADO イベント処理の詳細については、次を参照してください。 [ADO イベントを処理](../../../ado/guide/data/handling-ado-events.md)です。  
  
 確認して**Recordset**の境界を越えてオブジェクトは、**レコード セット**レコード ポインターを移動する前にします。 しようとする場合**MoveNext**とき**EOF** true または**MovePrev**とき**BOF** True の場合は、エラーが発生します。 いずれかを実行する場合、**移動**メソッドと両方**EOF**と**BOF** True は、エラーが生成されます。  
  
 などの操作を実行しようとする場合に、エラーも発生は**シーク**と**検索**、空で**レコード セット**です。
