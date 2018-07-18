---
title: レベル プロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28c5c9149d1734f410417df1d727b81e6e86ea1a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288048"
---
# <a name="level-properties"></a>レベル プロパティ 
  次の表では、ユーザー定義階層におけるレベルのプロパティの一覧および説明を示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|説明|レベルの説明を格納します。|  
|HideMemberIf|レベル内のメンバーをクライアント アプリケーションに対して非表示にするかどうかと、そのタイミングを示します。 このプロパティは、以下の値をとります。<br /><br /> Never<br /> メンバーは必ず表示されます。 これが既定値です。<br /><br /> OnlyChildWithNoName<br /> メンバーには、メンバーがその親の唯一の子とメンバーの名前が空の場合は表示されません。<br /><br /> OnlyChildWithParentName<br /> メンバーがその親の唯一の子で、メンバーの名前が親の名前と同じ場合、メンバーは表示されません。<br /><br /> NoName<br /> メンバーの名前が空の場合、メンバーは表示されません。<br /><br /> ParentName<br /> メンバーの名前がその親の名前と同じである場合、メンバーは表示されません。|  
|ID|レベルの一意の識別子 (ID) を格納します。|  
|名前|レベルの表示名を格納します。 既定では、レベルの名前はソース属性の名前と同じです。|  
|SourceAttribute|レベルの基になるソース属性の名前を格納します。|  
  
## <a name="see-also"></a>参照  
 [ユーザー階層プロパティ](user-hierarchies-properties.md)  
  
  
