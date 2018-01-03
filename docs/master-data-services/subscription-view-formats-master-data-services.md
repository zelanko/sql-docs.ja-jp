---
title: "サブスクリプション ビュー形式 (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff1e2566-ac8f-467d-a6d9-12c3f13879b9
caps.latest.revision: "9"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a29f3f006af3376c430b99de312474283905ed9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="subscription-view-formats-master-data-services"></a>サブスクリプション ビュー形式 (マスター データ サービス)
  選択するエンティティまたは派生階層に基づいて、次の形式をサブスクリプション ビューで使用できます。  
  
## <a name="subscription-view-formats"></a>サブスクリプション ビュー形式  
  
|[オブジェクト名]|Description|  
|----------|-----------------|  
|**リーフ メンバー**|リーフ メンバーとそのメンバーに関連付けられた属性値を含みます。|  
|**リーフ メンバー履歴**|リーフ メンバーの履歴データと関連付けられた属性値を含みます。 表示形式は、緩やかに変化を変更するディメンション タイプ 4 スタイルです。|  
|**リーフ メンバー SCD タイプ 2**|リーフ メンバーの履歴データ、現在のデータ、および関連付けられた属性値を含みます。 表示形式は、緩やかに変化するディメンション タイプ 2 スタイルです。|  
|**統合メンバー**|統合メンバーとそのメンバーに関連付けられた属性値を含みます。|  
|**統合メンバー履歴**|統合メンバーの履歴データと関連付けられた属性値を含みます。 表示形式は、緩やかに変化を変更するディメンション タイプ 4 スタイルです。|  
|**統合メンバー SCD タイプ 2**|統合メンバーの履歴データ、現在のデータ、および関連付けられた属性値を含みます。 表示形式は、緩やかに変化するディメンション タイプ 2 スタイルです。|  
|**コレクション メンバーシップ**|コレクションのリストとコレクションに関連付けられた属性値を含みます。|  
|**コレクション**|コレクションのリストと各コレクションのメンバーおよび重みの値と並べ替え順序を含みます。|  
|**コレクション メンバー履歴**|コレクション メンバーの履歴データと関連付けられた属性値を含みます。 表示形式は、緩やかに変化を変更するディメンション タイプ 4 スタイルです。|  
|**コレクション メンバー SCD タイプ 2**|コレクション メンバーの履歴データ、現在のデータ、および関連付けられた属性値を含みます。 表示形式は、緩やかに変化するディメンション タイプ 2 スタイルです。|  
|**明示的親子関係**|エンティティの明示的階層構造を親子形式で含みます。|  
|**明示的レベル**|エンティティの明示的階層構造をレベル形式で含みます。|  
|**派生親子関係 (派生階層ビュー)**|派生階層構造を親子形式で含みます。|  
|**派生レベル (派生階層ビュー)**|派生階層構造をレベル形式で含みます。|  
  
## <a name="see-also"></a>参照  
 [概要: データのエクスポート (マスター データ サービス)](../master-data-services/overview-exporting-data-master-data-services.md)   
 [サブスクリプション ビューを作成してデータをエクスポートする (マスター データ サービス)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
  
