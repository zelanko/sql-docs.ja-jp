---
title: "読み取り反復可能な分離レベルを使用してデッドロック |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 361a6c96a461dba4de6b5e72be6a5ec362affefb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>読み取り反復可能な分離レベルを使用してデッドロック
カスタム ビジネス オブジェクトは repeatable read の分離レベルを使用して、SQL Server へのアクセスをして、ビジネス オブジェクトが、クエリを送信し、同じトランザクションで更新する 2 つのクライアントで同時に呼び出されると、デッドロックは可能性があります。 リモート データ サービスが、デッドロックを解除する際にタイムアウトにプロセスの 1 つを許可するように設計されていますが、そのクライアントの更新プログラムは失敗します。  
  
 使用して、[カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)**コマンド タイムアウト**タイムアウトの長さを変更する動的なプロパティです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)



