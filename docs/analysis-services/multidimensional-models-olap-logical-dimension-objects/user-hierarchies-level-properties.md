---
title: レベルのプロパティ - ユーザー階層 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 903ece979d44dedd6353919af28bdb6c82986e16
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="user-hierarchies---level-properties"></a>ユーザー階層のレベルのプロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  次の表では、ユーザー定義階層におけるレベルのプロパティの一覧および説明を示します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|Description|レベルの説明を格納します。|  
|HideMemberIf|レベル内のメンバーをクライアント アプリケーションに対して非表示にするかどうかと、そのタイミングを示します。 このプロパティは、以下の値をとります。<br /><br /> Never<br /> メンバーは必ず表示されます。 これが既定値です。<br /><br /> OnlyChildWithNoName<br /> メンバーには、メンバーがその親の唯一の子メンバーの名前が空場合は表示されません。<br /><br /> OnlyChildWithParentName<br /> メンバーがその親の唯一の子で、メンバーの名前が親の名前と同じ場合、メンバーは表示されません。<br /><br /> NoName<br /> メンバーの名前が空の場合、メンバーは表示されません。<br /><br /> ParentName<br /> メンバーの名前がその親の名前と同じである場合、メンバーは表示されません。|  
|ID|レベルの一意の識別子 (ID) を格納します。|  
|名前|レベルの表示名を格納します。 既定では、レベルの名前はソース属性の名前と同じです。|  
|SourceAttribute|レベルの基になるソース属性の名前を格納します。|  
  
## <a name="see-also"></a>参照  
 [ユーザー階層プロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
