---
title: ページを使用する |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6542cb23deef9f10979e3bdb90c0820d84c0f150
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763033"
---
# <a name="using-pages"></a>ページを使用する
**PageCount**プロパティを使用して、**レコードセット**オブジェクトに含まれるデータのページ数を確認します。 *ページ*は、サイズが**PageSize**プロパティ設定と等しいレコードのグループです。 **PageSize**値よりも少数のレコードがあるため、最後のページが不完全な場合でも、 **PageCount**値の追加ページとしてカウントされます。 **Recordset**オブジェクトがこのプロパティをサポートしていない場合、 **PageCount**は、 **PageCount**がわからないであることを示す-1 になります。  
  
 データの論理ページを構成するレコードの数を確認するには、 **PageSize**プロパティを使用します。 ページサイズを設定すると、 **AbsolutePage**プロパティを使用して、特定のページの最初のレコードに移動できます。 これは、ユーザーがデータをページごとに表示し、一度に特定の数のレコードを表示できるようにする場合に、Web サーバーのシナリオで役立ちます。  
  
 このプロパティはいつでも設定でき、その値は特定のページの最初のレコードの位置を計算するために使用されます。  
  
 **AbsolutePage**プロパティを使用して、現在のレコードが配置されているページ番号を識別します。 ここでも、このプロパティを使用できるようにするには、プロバイダーが適切な機能をサポートしている必要があります。  
  
 **AbsolutePage**は1から始まる、現在のレコードが**レコードセット**内の最初のレコードの場合は1になります。 特定のページの最初のレコードに移動するには、このプロパティを設定します。 **PageCount**プロパティから合計ページ数を取得します。
