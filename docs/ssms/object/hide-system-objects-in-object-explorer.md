---
title: '[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする] | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 14e86dd976b86e61f7789d176998f9df0d70b47f
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67689992"
---
# <a name="hide-system-objects-in-object-explorer"></a>[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、オブジェクト エクスプローラーのシステム オブジェクトを非表示にする方法について説明します。 オブジェクト エクスプローラーの **[データベース]** ノードには、システム データベースなどのシステム オブジェクトが含まれています。 システム オブジェクトを非表示にするには、 **[ツール]** / **[オプション]** ページを使用します。 システム関数やシステム データ型など、システム オブジェクトの中にはこの設定で非表示にならないものもあります。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a>オブジェクト エクスプローラーでシステム オブジェクトを非表示にするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[環境/スタートアップ]** ページで、 **[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]** を選択し、 **[OK]** をクリックします。  
  
3.  この変更を有効にするには SQL Server Management Studio の再起動が必要であることを示すメッセージが表示されたら、 **[SQL Server Management Studio]** ダイアログ ボックスで **[OK]** をクリックします。  
  
4.  SQL Server Management Studio を閉じ、再度開きます。  
  
