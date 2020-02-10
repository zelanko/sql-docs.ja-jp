---
title: 'タスク 7: 複合ドメインを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bbc00117e10e48adbde37b9f0561610feff8f87e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65488963"
---
# <a name="task-7-creating-a-composite-domain"></a>タスク 7: 複合ドメインを作成する
  このタスクでは、address **Line**、 **City**、 **State**、および**Zip**の各ドメインで構成される、**アドレス検証**という複合ドメインを作成します。 複合ドメインでは、ルール内の複数のドメインに関するクロスドメイン ルールを定義できます。 複合ドメインには、フィールド値を複数のドメインに解析できるなどの利点があります。  たとえば、氏名フィールドの値を、名、ミドル ネーム、および姓の個別のドメインに解析できます。 このチュートリアルでは、クロスドメイン ルールのみを定義します。 詳細について[は、「複合ドメインの管理](https://msdn.microsoft.com/library/hh510399.aspx)」を参照してください。  
  
1.  左側のウィンドウで、ツールバーの [**複合ドメインの作成**] ボタンをクリックします。  
  
     ![[複合ドメインの作成] ツール バー ボタン](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "[複合ドメインの作成] ツール バー ボタン")  
  
2.  **複合ドメイン名**の**アドレス検証**を入力します。  
  
     ![アドレス検証複合ドメイン](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "アドレス検証複合ドメイン")  
  
3.  [ドメイン] ボックスの一覧から [ **Address Line**]、[ **City**]、[ **State**]、および [ **Zip** ] を選択し、**右矢印**をクリックして [**複合ドメイン内のドメイン**] の一覧に追加します。  
  
4.  [**OK**] をクリックして、ダイアログ ボックスを閉じます。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 8: 複合ドメイン ルールを作成する](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
