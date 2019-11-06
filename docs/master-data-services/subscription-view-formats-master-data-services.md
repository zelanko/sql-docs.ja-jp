---
title: サブスクリプション ビュー形式 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ff1e2566-ac8f-467d-a6d9-12c3f13879b9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ba0152d37b1a050c1e46594ab8a5820606b116c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085613"
---
# <a name="subscription-view-formats-master-data-services"></a>サブスクリプション ビュー形式 (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  選択するエンティティまたは派生階層に基づいて、次の形式をサブスクリプション ビューで使用できます。  
  
## <a name="subscription-view-formats"></a>サブスクリプション ビュー形式  
  
|名前|説明|  
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
  
## <a name="see-also"></a>関連項目  
 [概要:データのエクスポート (マスター データ サービス)](../master-data-services/overview-exporting-data-master-data-services.md)   
 [サブスクリプション ビューを作成してデータをエクスポートする (マスター データ サービス)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
  
