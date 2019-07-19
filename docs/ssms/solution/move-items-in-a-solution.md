---
title: ソリューションのアイテムの移動 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 217ad4a4d045798adaa7d430b0b91ba2eb3e8d7c
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67689805"
---
# <a name="move-items-in-a-solution"></a>ソリューションのアイテムの移動
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] プロジェクトに含まれるプロジェクト アイテムには、クエリ、接続、およびその他のファイルがあります。 クエリとその他のファイルはソリューション エクスプローラーで別のプロジェクトに移動することができますが、接続は移動できません。  
  
### <a name="to-move-items-in-solution-explorer"></a>ソリューション エクスプローラーでアイテムを移動するには  
  
1.  ソリューション エクスプローラーで、移動するアイテムを選択します。  
  
2.  **[編集]** メニューの **[切り取り]** をクリックします。  
  
3.  ソリューション エクスプローラーで、移動先を選択します。  
  
4.  **[編集]** メニューの **[貼り付け]** をクリックします。  
  
ソリューション エクスプローラー内でクエリやその他のファイルをドラッグして、アイテムを移動することもできます。 アイテムをドラッグする場合は、ドラッグ操作の結果を目で見て確認できます。 クエリを別の種類のプロジェクトに移動する場合、そのクエリが移動先のプロジェクトでその他のファイルと見なされることがあります。  
  
> [!NOTE]  
> 接続を指定したクエリを移動しても、接続は移動先のプロジェクトに移動しません。 クエリを別のプロジェクトに移動すると、接続の設定は消去されます。  
  
## <a name="see-also"></a>参照  
[ソリューション エクスプローラー](../../ssms/solution/solution-explorer.md)  
[ソリューションの項目のコピー](../../ssms/solution/copy-items-in-a-solution.md)  
  
