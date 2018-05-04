---
title: レコード セットを配置 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c65a8da00ea92feadc21d0fd1ce3a28967d9a259
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-positioning"></a>レコード セットを配置
使用して、 **AbsolutePosition**内の序数位置に基づいて、レコードに移動するプロパティ、**レコード セット**オブジェクト、または現在のレコードの序数位置を決定します。 プロバイダーは、このプロパティを使用するための適切な機能をサポートする必要があります。  
  
 **AbsolutePosition**は 1 に基づいており、現在のレコードが最初のレコードが 1 と等しい、 **Recordset**です。 前述のように、内のレコードの合計数を取得することができます、 **Recordset**オブジェクトから、 **RecordCount**プロパティです。  
  
 設定すると、 **AbsolutePosition**プロパティ、現在のキャッシュ内のレコードになっている場合でも ADO キャッシュに再読み込みする指定されたレコードで始まるレコードの新しいグループにします。 **CacheSize**プロパティは、このグループのサイズを決定します。  
  
> [!NOTE]
>  使用しないで、 **AbsolutePosition**サロゲート レコード番号としてのプロパティです。 前のレコードを削除すると、特定のレコードの位置を変更します。 特定のレコードと同じことが保証されていません**AbsolutePosition**場合、 **Recordset**オブジェクトを再クエリまたは再び開きます。 ブックマークが保持して、指定された位置を返すための推奨される方法し、すべての種類の唯一の方法は、 **Recordset**オブジェクト。
