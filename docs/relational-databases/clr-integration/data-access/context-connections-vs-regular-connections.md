---
title: 通常の接続とコンテキスト接続 |マイクロソフトドキュメント
description: SQL Server では、Transact-SQL ステートメントに通常の接続を使用する必要がある場合がありますが、コンテキスト接続にはパフォーマンスとリソースの使用上の利点があります。
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485267"
---
# <a name="context-connections-vs-regular-connections"></a>コンテキスト接続と通常の接続
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  リモート サーバーに接続している場合は、常に、コンテキスト接続ではなく通常の接続を使用します。 ストアド プロシージャや関数を実行している同一サーバーに接続する必要がある場合は、ほとんどの場合、コンテキスト接続を使用します。 コンテキスト接続には、同一のトランザクション領域で実行され、再認証が不要であるなどの利点があります。  
  
 また、コンテキスト接続を使用すると、通常、パフォーマンスが向上し、リソースの使用が抑えられます。 コンテキスト接続はインプロセス専用接続であるため、ネットワーク プロトコルとトランスポート層をバイパスして Transact-SQL ステートメントを送信し、結果を受信することで、サーバーに直接接続できます。 認証プロセスも同様に迂回されます。 次の図は **、SqlClient**マネージ プロバイダーの主要なコンポーネントと、通常の接続を使用するとき、およびコンテキスト接続を使用する場合に、さまざまなコンポーネントが相互にやり取りする方法を示しています。  
  
 ![コンテキストと通常の接続のコード パス](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "コンテキストと通常の接続のコード パス")  
  
 コンテキスト接続で使用するコード パスは、通常の接続よりも短く、関連するコンポーネントの数も少ないので、サーバーへの要求とサーバーからの結果の取得が通常の接続よりも速くなることが期待できます。 サーバーでのクエリの実行時間は、どちらの接続でも同じです。  
  
 同じサーバーに対して通常の接続を別に開く必要が生じる場合もあります。 たとえば、コンテキスト接続の使用には、[通常の接続とコンテキスト接続に関する制限で説明されている特定の制限があります](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)。  
  
## <a name="see-also"></a>参照  
 [コンテキスト接続](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
