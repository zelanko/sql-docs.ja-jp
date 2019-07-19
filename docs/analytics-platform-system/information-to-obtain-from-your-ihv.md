---
title: IHV - Analytics Platform System から情報を取得 |Microsoft Docs
description: Analytics Platform System appliance に関する IHV から取得する情報。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 016a20567968e45456be79c8c67e77d7c3fbb2bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960832"
---
# <a name="information-to-obtain-from-your-ihv"></a>IHV から取得する情報
独立系ハードウェア ベンダー (IHV) は、新しい SQL Server PDW アプライアンスを提供する、ときに、アプライアンス上の実行が完了、アプライアンスのハードウェアおよび構成情報は提供もします。 この情報をご使用のアプライアンスを管理する必要があります。  
  
IHV から通常に必要な情報を次に示します。 場合によっては、追加、またはその他の情報が必要です。 IHV アプライアンスの配信を使用したすべての関連情報が転送されるされているかどうかを確認するかどうか。  
  
|||  
|-|-|  
|**情報またはドキュメント**|**[説明]**|  
|部品表 (BOM)|部品の表では、アプライアンスに含まれているコンポーネントが一覧表示します。 この情報は、すべてのコンポーネントが配信されたことを確認する必要があります。<br /><br />**重要:** 部品の表は、各ラック全体と各アプライアンス ノードの重みを含める必要があります。 処理し、アプライアンスのコンポーネントを移動する方法を計画するときに、この情報は重要なと、データ センターを確認する場合、アプライアンスに対応できます。 BOM にノードの重みが含まれていない場合は、すべてのノード、IHV から取得した情報を確認します。|  
|ケーブル配線図|ケーブル配線図では、ラック、ネットワーク、電力、およびアプライアンスごとにその他のケーブルを接続する方法を示します。 これらの図は、データ センターでアプライアンスをインストールするときに必要なし、いつでも削除するか、コンポーネントを交換する必要があります。|  
|アプライアンスのラックの要件|アプライアンスをインストールするには、データ センターで、通気およびサイズと、アプライアンスのケーブルの長さの要件とコンポーネントの電源の要件、データ センターを満たしているかどうかを把握する必要があります。 参照 Bill of Materials (BOM) の上、アプライアンス コンポーネントの重量についても必要ですが。|  
  
