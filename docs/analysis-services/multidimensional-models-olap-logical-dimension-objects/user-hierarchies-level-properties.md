---
title: レベルのプロパティ - ユーザー階層 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 230ec186562c99b2851c18e910474c207698d300
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209212"
---
# <a name="user-hierarchies---level-properties"></a>ユーザー階層 - レベルのプロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  次の表では、ユーザー定義階層におけるレベルのプロパティの一覧および説明を示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|説明|レベルの説明を格納します。|  
|HideMemberIf|レベル内のメンバーをクライアント アプリケーションに対して非表示にするかどうかと、そのタイミングを示します。 このプロパティは、以下の値をとります。<br /><br /> しない<br /> メンバーは必ず表示されます。 これは既定値です。<br /><br /> OnlyChildWithNoName<br /> メンバーには、メンバーがその親の唯一の子とメンバーの名前が空の場合は表示されません。<br /><br /> OnlyChildWithParentName<br /> メンバーがその親の唯一の子で、メンバーの名前が親の名前と同じ場合、メンバーは表示されません。<br /><br /> NoName<br /> メンバーの名前が空の場合、メンバーは表示されません。<br /><br /> ParentName<br /> メンバーの名前がその親の名前と同じである場合、メンバーは表示されません。|  
|ID|レベルの一意の識別子 (ID) を格納します。|  
|名前|レベルの表示名を格納します。 既定では、レベルの名前はソース属性の名前と同じです。|  
|SourceAttribute|レベルの基になるソース属性の名前を格納します。|  
  
## <a name="see-also"></a>関連項目  
 [ユーザー階層プロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
