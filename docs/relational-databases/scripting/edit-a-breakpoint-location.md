---
title: ブレークポイントの位置の編集 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology:
- database-engine
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.location.file
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6590f4514a08773da5e31763b62e273ef8c83da3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="edit-a-breakpoint-location"></a>ブレークポイントの位置の編集
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  ブレークポイントの位置では、ブレークポイントを設定する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイル内の行や文字を指定します。 ブレークポイントの位置を編集して、ブレークポイントを別の位置や別のスクリプトに移動できます。  
  
## <a name="editing-a-location"></a>位置の編集  
 ブレークポイントの位置を編集すると、ブレークポイントはヒット カウント、条件などの既存のすべてのプロパティと共に新しい位置に移動します。  
  
#### <a name="to-edit-a-breakpoint-location"></a>ブレークポイントの位置を編集するには  
  
1.  エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[場所]** をクリックします。  
  
     - または -  
  
     **[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[場所]** をクリックします。  
  
2.  **[ファイルのブレークポイント]** ダイアログ ボックスで、新しいファイルを指定するには **[ファイル]** 、新しい行を指定するには **[行]** 、行内の新しい場所を指定するには **[文字]** の各項目を編集します。 指定した新しいファイルがクエリ エディター ウィンドウで既に開いている場合は、ブレークポイントがそのエディター ウィンドウに移動します。 ファイルが開いていない場合は、新しいクエリ エディター ウィンドウが開き、そのファイルが読み込まれ、ブレークポイントが新しい位置に移動します。  
  
     **をデバッグする場合、** [元のバージョンと異なるソース コードを許可する] [!INCLUDE[tsql](../../includes/tsql-md.md)]オプションは無効です。  
  
## <a name="see-also"></a>参照  
 [ヒット カウントの指定](../../relational-databases/scripting/specify-a-hit-count.md)   
 [ブレークポイント アクションの指定](../../relational-databases/scripting/specify-a-breakpoint-action.md)   
 [ブレークポイント条件の指定](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [ブレークポイント フィルターの指定](../../relational-databases/scripting/specify-a-breakpoint-filter.md)  
  
  
