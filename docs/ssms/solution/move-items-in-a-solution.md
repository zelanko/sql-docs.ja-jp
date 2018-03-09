---
title: "ソリューションのアイテムの移動 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-solutions
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d56df29ee9a9db55e3c5b5c0cc645b7dc5b9c9a9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="move-items-in-a-solution"></a>ソリューションのアイテムの移動
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] プロジェクトに含まれるプロジェクト アイテムには、クエリ、接続、およびその他のファイルがあります。 クエリとその他のファイルはソリューション エクスプローラーで別のプロジェクトに移動することができますが、接続は移動できません。  
  
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
  
