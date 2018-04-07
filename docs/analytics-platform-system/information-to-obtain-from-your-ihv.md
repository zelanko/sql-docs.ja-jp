---
title: については、IHV (Analytics Platform System) から取得するには
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bce301a-704c-4236-a0a1-851bd17e2b6c
caps.latest.revision: 11
ms.openlocfilehash: 384a4051df1596dc334a78a751cb7954f512e8d5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="information-to-obtain-from-your-ihv"></a>については、IHV から取得するには
独立系ハードウェア ベンダー (IHV) に、新しい SQL Server PDW アプライアンスを配信する際、アプライアンス上の実行が、アプライアンスのハードウェアおよび構成情報は提供もいます。 この情報をアプライアンスを管理する必要があります。  
  
次の一覧は、IHV から通常必要な情報を示します。 場合によっては、追加情報やその他の情報が必要です。 IHV アプライアンス配信に関するすべての関連情報が転送されるされているかどうかを確認してください。  
  
|||  
|-|-|  
|**情報またはドキュメント**|**Description**|  
|部品表 (BOM)|部品の表では、アプライアンスに含まれているコンポーネントが一覧表示します。 この情報は、すべてのコンポーネントが配信されたことを確認する必要があります。<br /><br />**重要:**部品の表は各アプライアンス ノードの完全な各ラックの重みを含める必要があります。 処理し、アプライアンス コンポーネントを移動する方法を計画する際に、この情報は重要とアプライアンスが、データ センターを確認する場合に対応できます。 BOM にノードの重みが含まれていない場合は、すべてのノードに対して、IHV からこの情報を取得してください。|  
|ケーブル配線図|ケーブル配線図では、ラック、ネットワーク、出力、およびアプライアンスごとにその他のケーブルを接続する方法を示します。 これらの図は、データ センターにアプライアンスをインストールするときに必要なし、いつでも削除するか、コンポーネントの交換する必要があります。|  
|アプライアンスのラックの要件|アプライアンスは、データ センターにインストールすることができます、前に、データ センターがエアフローおよびサイズと同様に、アプライアンスのケーブルの長さの要件とコンポーネントの電源の要件を満たしているかどうかを把握する必要があります。 参照 Bill of Materials (BOM) の上アプライアンス部品の重量についても必要になります。|  
  
