---
title: '[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e039446191154144dd6660fa6e8d3b4b65d1013
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067315"
---
# <a name="hide-system-objects-in-object-explorer"></a>[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、オブジェクト エクスプローラーのシステム オブジェクトを非表示にする方法について説明します。 オブジェクト エクスプローラーの **[データベース]** ノードには、システム データベースなどのシステム オブジェクトが含まれています。 システム オブジェクトを非表示にするには、 **[ツール]** / **[オプション]** ページを使用します。 システム関数やシステム データ型など、システム オブジェクトの中にはこの設定で非表示にならないものもあります。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a>オブジェクト エクスプローラーでシステム オブジェクトを非表示にするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[環境/スタートアップ]** ページで、 **[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]** を選択し、 **[OK]** をクリックします。  
  
3.  この変更を有効にするには SQL Server Management Studio の再起動が必要であることを示すメッセージが表示されたら、 **[SQL Server Management Studio]** ダイアログ ボックスで **[OK]** をクリックします。  
  
4.  SQL Server Management Studio を閉じ、再度開きます。  
  
  
