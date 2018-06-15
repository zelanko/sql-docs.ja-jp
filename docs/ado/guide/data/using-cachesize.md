---
title: CacheSize を使用して |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], CacheSize property
- CacheSize property [ADO]
ms.assetid: ca1c3422-b6a4-4ba6-af55-54f975b698b1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f15c7ba0e954f6214670a3ba687094131e90a57
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273261"
---
# <a name="using-cachesize"></a>CacheSize を使用します。
使用して、 **CacheSize**プロパティは、プロバイダーからローカル メモリに一度に取得するレコードの数を制御します。 たとえば場合、 **CacheSize**は 10 ですが最初に開く後、**レコード セット**オブジェクト、プロバイダーがローカル メモリに最初の 10 個のレコードを取得します。 間を移動すると、 **Recordset**オブジェクト、プロバイダーがローカル メモリ バッファーからデータを返します。 過去のキャッシュの最後のレコードを移動するとすぐに、プロバイダーは、キャッシュにデータ ソースから、次の 10 個のレコードを取得します。  
  
> [!NOTE]
>  **CacheSize**に基づく、**開いている行の最大数**プロバイダー固有のプロパティ (で、**プロパティ**のコレクション、 **Recordset**オブジェクト)。 設定することはできません**CacheSize**より大きい値に**開いている行の最大数。** プロバイダーで開くことができる行の数を変更するには、次のように設定します。**最大行数は開いている**です。  
  
 値**CacheSize**の有効期間中に調整されることができます、 **Recordset**データ ソースから次に、キャッシュ内のレコードの数にのみ影響、オブジェクトがこの値を変更します。 プロパティの値のみを変更しても、キャッシュの現在の内容は変更されません。  
  
 も取得するレコードが少ない場合**CacheSize**を示す、プロバイダーは、残りのレコードを返し、エラーは発生しません。  
  
 A **CacheSize**ゼロに設定は許可されていませんし、エラーが返されます。  
  
 キャッシュから取得したレコードでは、他のユーザーが、ソース データに対する同時変更は反映されません。 すべてのキャッシュされたデータの更新を強制するを使用して、[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドです。  
  
 場合**CacheSize**ナビゲーション方法 1 より大きい値に設定されます ([移動](../../../ado/reference/ado-api/move-method-ado.md)、 [MoveFirst、MoveLast、MoveNext、および MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md))、削除されたへの移動されない可能性がありますレコードを取得した後、削除が発生した場合に記録します。 最初のフェッチ後以降の削除は反映されませんデータ キャッシュ内の削除された行のデータ値にアクセスしようとするまで。 ただし、設定**CacheSize**を 1 に削除された行はフェッチできないためにこの問題を排除します。
