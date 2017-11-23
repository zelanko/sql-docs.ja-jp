---
title: "種類のカーソル (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: cursors [ADO], types
ms.assetid: 7cc01544-e814-403b-bbfe-a2750bf921bd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c8ab039bfe5754587e3f7adda36c0b715138d65
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="types-of-cursors-ado"></a>種類のカーソル (ADO)
一般的な規則として、アプリケーションは、必要なデータ アクセスを提供する最も簡単なカーソルを使用する必要があります。 基本の (順方向専用、読み取り専用、静的、スクロール、バッファーを使用しない) 場合は、各追加カーソル特性には、価格、クライアントのメモリ、ネットワークの負荷、またはパフォーマンス。 多くの場合は、既定のカーソル オプションは、アプリケーションが実際に必要なよりも複雑なカーソルを生成します。  
  
 カーソルの種類の選択とに依存アプリケーションが、結果セットを使用する方法もいくつか設計の考慮事項の結果セット、使用する可能性の高いデータの割合、データの変更、およびアプリケーションのパフォーマンスに小文字の区別のサイズを含む要件。  
  
 最も基本的なカーソル選択によって異なるかどうかを変更または単にデータを表示する必要があります。  
  
-   変更データを除く、結果のセットをスクロールする場合を使用して、[順方向専用](../../../ado/guide/data/forward-only-cursors.md)または[静的](../../../ado/guide/data/static-cursors.md)カーソル。  
  
-   大きな結果セットおよび少数の行を選択する必要がある場合を使用して、[キーセット](../../../ado/guide/data/keyset-cursors.md)カーソル。  
  
-   使用して、結果セットを最新に追加し、変更されると、し、すべての同時実行ユーザーが削除を同期する場合、[動的](../../../ado/guide/data/dynamic-cursors.md)カーソル。  
  
 各カーソルの種類は見えますと区別する、これらの種類のカーソルいないこと、程度異なる種類だけで重複する特性やオプションの結果として注意してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [順方向専用カーソル](../../../ado/guide/data/forward-only-cursors.md)  
  
-   [静的カーソル](../../../ado/guide/data/static-cursors.md)  
  
-   [Keyset カーソル](../../../ado/guide/data/keyset-cursors.md)  
  
-   [動的カーソル](../../../ado/guide/data/dynamic-cursors.md)  
  
## <a name="see-also"></a>参照  
 [順方向専用カーソル](../../../ado/guide/data/forward-only-cursors.md)   
 [静的カーソル](../../../ado/guide/data/static-cursors.md)   
 [Keyset カーソル](../../../ado/guide/data/keyset-cursors.md)   
 [動的カーソル](../../../ado/guide/data/dynamic-cursors.md)
