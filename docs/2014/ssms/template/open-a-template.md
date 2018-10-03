---
title: テンプレートを開く | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 940a5a220001ed682bf3972db60bac47b870140d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078463"
---
# <a name="open-a-template"></a>テンプレートを開く
  テンプレート エクスプローラーからテンプレートを開くことができます。  
  
## <a name="to-open-a-template-from-template-explorer"></a>テンプレート エクスプローラーからテンプレートを開くには  
 テンプレート エクスプローラーからテンプレートを開くことができます。  
  
1.  テンプレート エクスプローラーを開くには、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  テンプレート カテゴリの一覧で、開こうとしているテンプレートを含むカテゴリを展開します。  
  
3.  テンプレートを開くには、次の 3 とおりの方法があります。  
  
    1.  テンプレートをダブルクリックしてコード エディター ウィンドウで開きます。  
  
    2.  テンプレートを右クリックして **[開く]** を選択し、コード エディター ウィンドウで開きます。  
  
    3.  テンプレートをコード エディター ウィンドウにドラッグし、テンプレート コードをエディター ウィンドウの内容に追加します。  
  
 テンプレートを開いた後、 **[テンプレート パラメーターの値の指定]** ダイアログ ボックスでテンプレート パラメーターを適切な値に置き換えます。  
  
 テンプレートを開いて新しいエディター ウィンドウが起動する場合、そのウィンドウは、現在のアクティブな接続の資格情報によって開きます。 たとえば、CREATE DATABASE テンプレートを開くときに、オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスにフォーカスがあると、そのインスタンスへの接続を使用して新しいエディター ウィンドウが開きます。 アクティブな接続がない場合は、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によってログイン ダイアログが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [テンプレート エクスプ ローラー](template-explorer.md)   
 [テンプレート パラメーターの置換](replace-template-parameters.md)  
  
  
