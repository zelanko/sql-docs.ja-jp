---
title: ページを使用して |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6afd68ddf99799288939eeb0c6522275ec4d273f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704540"
---
# <a name="using-pages"></a>ページを使用する
使用して、 **PageCount**プロパティのデータの数ページには、**レコード セット**オブジェクト。 *ページ*レコードと同じサイズのグループ、 **PageSize**プロパティの設定。 少ないレコードがあるため、最後のページが完了しない場合でも、 **PageSize**で追加のページとしてカウントされますが、値、 **PageCount**値。 場合、 **Recordset**オブジェクトは、このプロパティをサポートしていません**PageCount**ことを示す-1 になります、 **PageCount**決められていません。  
  
 使用して、 **PageSize**プロパティをレコードの数は、データの論理ページを構成を確認します。 ページ サイズの確立を使用することができます、 **AbsolutePage**プロパティを特定のページの最初のレコードに移動します。 これは、一度にレコード数を表示するデータをページにユーザーを許可する場合、Web サーバーのシナリオで役に立ちます。  
  
 このプロパティは、いつでも設定でき、特定のページの最初のレコードの位置を計算するための値が使用されます。  
  
 使用して、 **AbsolutePage**プロパティを現在のレコードが配置されているページ数を特定します。 ここでも、プロバイダーは、このプロパティを使用するための適切な機能をサポートする必要があります。  
  
 **AbsolutePage**は 1 に基づいており、現在のレコードが最初のレコードは 1 に等しい、 **Recordset**します。 特定のページの最初のレコードに移動するには、このプロパティを設定します。 ページの合計数を取得、 **PageCount**プロパティ。
