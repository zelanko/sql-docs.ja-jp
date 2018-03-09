---
title: "ページを使用して |Microsoft ドキュメント"
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
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd893e19c1ab5ac5a4dd657ce61ef76295f2b188
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="using-pages"></a>ページを使用します。
使用して、 **PageCount**プロパティ内のデータのページ数を調べること、 **Recordset**オブジェクト。 *ページ*レコードと同じサイズのグループ、 **PageSize**プロパティの設定。 も少ないレコードがあるため、最後のページが完了していない場合でも、 **PageSize**値で追加のページとして数えられます、 **PageCount**値。 場合、 **Recordset**オブジェクトは、このプロパティをサポートしていません**PageCount**ことを示す-1 になります、 **PageCount**決められていません。  
  
 使用して、 **PageSize**データの論理ページを構成するレコード数を決定するプロパティです。 使用するページ サイズを確立することができます、**と、AbsolutePage**プロパティを特定のページの最初のレコードに移動します。 これは、一度にレコード数を表示する、データのページにユーザーを許可するときに Web サーバーのシナリオで役に立ちます。  
  
 このプロパティは、いつでも設定でき、特定のページの最初のレコードの場所を計算するための値が使用されます。  
  
 使用して、**と、AbsolutePage**プロパティを現在のレコードが配置されているページ数を指定します。 もう一度、プロバイダーは、このプロパティを使用するための適切な機能をサポートする必要があります。  
  
 **AbsolutePage**は 1 に基づいており、現在のレコードが最初のレコードが 1 と等しい、 **Recordset**です。 特定のページの最初のレコードに移動するには、このプロパティを設定します。 ページの合計数を取得、 **PageCount**プロパティです。
