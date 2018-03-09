---
title: "データを更新し、永続化 |Microsoft ドキュメント"
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
- updating data [ADO]
- data updates [ADO]
- ADO, updating data
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1fd0fc64e1727b5e4ba9d2830218f3ddb6e004be
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="updating-and-persisting-data"></a>更新およびデータを保持します。
前のチャプターは、ADO を使用して、データ ソース内のデータを取得する方法、データ内を移動する方法、およびデータを編集する方法も説明してきました。 もちろん場合は、アプリケーションの目的は、データを変更するユーザーを許可するのには、これらの変更を保存する方法を理解する必要があります。 永続化することができますか、 **Recordset**を使用してファイルを変更、**保存**メソッド、または、その変更を使用してストレージのデータ ソースに戻すを送信できます、**更新**または**UpdateBatch**メソッドです。  
  
 複数の行のデータを変更する前の章で、 **Recordset**です。 ADO では、追加、削除、および行のデータの変更に関連する 2 つの基本的な概念をサポートします。  
  
 最初の概念はすぐに変更する、**レコード セット**。 代わりに、内部に行われる*コピー バッファー*です。 変更を保持する場合は、コピー バッファー内の変更は破棄されます。 コピー バッファー内の変更を適用、変更を保持する場合、 **Recordset**です。  
  
 2 番目の概念は、操作を宣言する行を完了するとすぐに変更がデータ ソースに反映するか (つまり、*即時*モード)、または一連の行に対するすべての変更が、セットの操作を宣言するまでに収集されます完全な (つまり、*バッチ*モード)。 **LockType**プロパティは、基になるデータ ソースに変更を適用する場合を決定します。 **adLockOptimistic**または**adLockPessimistic**イミディ エイト モードを指定します、 **adLockBatchOptimistic**バッチ モードを指定します。 **CursorLocation**プロパティに関係が**LockType**の設定を使用します。 インスタンス、 **adLockPessimistic**場合の設定はサポートされていません、 **CursorLocation**プロパティに設定されている**adUseClient**です。  
  
 イミディ エイト モードの各呼び出しで、**更新**メソッドは、データ ソースへの変更を伝達します。 バッチ モードの各呼び出しで**更新**現在の行位置の移動、コピー バッファーにのみ、変更を保存するか、 **UpdateBatch**メソッドは、データ ソースへの変更を伝達します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [データの更新](../../../ado/guide/data/updating-data.md)  
  
-   [データの保持](../../../ado/guide/data/persisting-data.md)
