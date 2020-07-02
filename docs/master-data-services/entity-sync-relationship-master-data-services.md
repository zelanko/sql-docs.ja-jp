---
title: エンティティの同期関係
description: エンティティの同期は、エンティティのバージョン間で反復可能な一方向の同期であり、マスターデータサービスモデル間でエンティティデータを共有できます。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0dac91e4f43d244e133511e792f29770949da905
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811944"
---
# <a name="entity-sync-relationship-master-data-services"></a>エンティティの同期関係 [マスター データ サービス]

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  エンティティ同期は、エンティティのバージョン間での反復可能な一方向の同期です。 異なるモデルの間でエンティティ データを共有できます。 1 つのモデルで唯一の情報源を保持し、このマスター データをその他のモデルで再利用できます。 たとえば、1 つのモデル エンティティに米国の状態データを格納し、その他のモデルでそのデータを再利用できます。  
  
 エンティティの同期では、データのワンタイム コピーを行うこともできます。  
  
 同期の実行中に、自由形式のリーフ メンバーとソース エンティティ内のファイル属性がすべてターゲット エンティティに同期されます。 これにより、エンティティ スキーマとメンバーが作成、削除、変更されます。  
  
 一度同期関係が確立されると、ターゲット エンティティは同期プロセスによってのみ変更できます。 同期関係はいつでも削除して、ターゲット エンティティを編集可能にできます。  
  
## <a name="see-also"></a>関連項目  
 [エンティティの同期関係を作成して実行する &#40;マスターデータサービス&#41;](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [エンティティの同期関係の編集と削除 (マスター データ サービス)](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
