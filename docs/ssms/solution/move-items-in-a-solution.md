---
title: "ソリューションのアイテムの移動 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b0140646e92871aa5d3ab2acbb95b417ab38d28b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="move-items-in-a-solution"></a>ソリューションのアイテムの移動
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] プロジェクトに含まれるプロジェクト アイテムには、クエリ、接続、およびその他のファイルがあります。 クエリとその他のファイルはソリューション エクスプローラーで別のプロジェクトに移動することができますが、接続は移動できません。  
  
### <a name="to-move-items-in-solution-explorer"></a>ソリューション エクスプローラーでアイテムを移動するには  
  
1.  ソリューション エクスプローラーで、移動するアイテムを選択します。  
  
2.  **[編集]** メニューの **[切り取り]**をクリックします。  
  
3.  ソリューション エクスプローラーで、移動先を選択します。  
  
4.  **[編集]** メニューの **[貼り付け]**をクリックします。  
  
ソリューション エクスプローラー内でクエリやその他のファイルをドラッグして、アイテムを移動することもできます。 アイテムをドラッグする場合は、ドラッグ操作の結果を目で見て確認できます。 クエリを別の種類のプロジェクトに移動する場合、そのクエリが移動先のプロジェクトでその他のファイルと見なされることがあります。  
  
> [!NOTE]  
> 接続を指定したクエリを移動しても、接続は移動先のプロジェクトに移動しません。 クエリを別のプロジェクトに移動すると、接続の設定は消去されます。  
  
## <a name="see-also"></a>参照  
[ソリューション エクスプローラー](../../ssms/solution/solution-explorer.md)  
[ソリューションの項目のコピー](../../ssms/solution/copy-items-in-a-solution.md)  
  

