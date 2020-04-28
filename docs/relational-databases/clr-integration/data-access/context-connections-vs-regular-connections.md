---
title: 標準接続とコンテキスト接続 |Microsoft Docs
description: SQL Server では、Transact-sql ステートメントに通常の接続を使用する必要がある場合がありますが、コンテキスト接続はパフォーマンスとリソースの使用に関する利点を提供します。
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: 881b7463400665d22baaa9b19f13cb5949df0830
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81485267"
---
# <a name="context-connections-vs-regular-connections"></a>コンテキスト接続と標準接続の比較
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  リモート サーバーに接続している場合は、常に、コンテキスト接続ではなく通常の接続を使用します。 ストアド プロシージャや関数を実行している同一サーバーに接続する必要がある場合は、ほとんどの場合、コンテキスト接続を使用します。 コンテキスト接続には、同一のトランザクション領域で実行され、再認証が不要であるなどの利点があります。  
  
 また、コンテキスト接続を使用すると、通常、パフォーマンスが向上し、リソースの使用が抑えられます。 コンテキスト接続はインプロセスのみの接続であるため、ネットワークプロトコルとトランスポート層をバイパスして Transact-sql ステートメントを送信し、結果を受け取ることによって、サーバーに直接接続できます。 認証プロセスも同様に迂回されます。 次の図は、 **SqlClient**マネージプロバイダーの主要なコンポーネントを示しています。また、通常の接続を使用している場合や、コンテキスト接続を使用している場合は、コンポーネント間の相互作用についても説明しています。  
  
 ![コンテキストと通常の接続のコード パス](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "コンテキストと通常の接続のコード パス")  
  
 コンテキスト接続で使用するコード パスは、通常の接続よりも短く、関連するコンポーネントの数も少ないので、サーバーへの要求とサーバーからの結果の取得が通常の接続よりも速くなることが期待できます。 サーバーでのクエリの実行時間は、どちらの接続でも同じです。  
  
 同じサーバーに対して通常の接続を別に開く必要が生じる場合もあります。 たとえば、コンテキスト接続の使用には、[通常の接続とコンテキスト接続に関する制限](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)事項で説明されているような制限があります。  
  
## <a name="see-also"></a>参照  
 [コンテキスト接続](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
