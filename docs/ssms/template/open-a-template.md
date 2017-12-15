---
title: "テンプレートを開く | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-templates
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ce156b9166ceb7b6607670e316d575599019bbc
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="open-a-template"></a>テンプレートを開く
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] テンプレート エクスプローラーからテンプレートを開くことができます。  
  
## <a name="to-open-a-template-from-template-explorer"></a>テンプレート エクスプローラーからテンプレートを開くには  
テンプレート エクスプローラーからテンプレートを開くことができます。  
  
1.  テンプレート エクスプローラーを開くには、 **[表示]** メニューの **[テンプレート エクスプローラー]**をクリックします。  
  
2.  テンプレート カテゴリの一覧で、開こうとしているテンプレートを含むカテゴリを展開します。  
  
3.  テンプレートを開くには、次の 3 とおりの方法があります。  
  
    1.  テンプレートをダブルクリックしてコード エディター ウィンドウで開きます。  
  
    2.  テンプレートを右クリックして **[開く]** を選択し、コード エディター ウィンドウで開きます。  
  
    3.  テンプレートをコード エディター ウィンドウにドラッグし、テンプレート コードをエディター ウィンドウの内容に追加します。  
  
テンプレートを開いた後、 **[テンプレート パラメーターの値の指定]** ダイアログ ボックスでテンプレート パラメーターを適切な値に置き換えます。  
  
テンプレートを開いて新しいエディター ウィンドウが起動する場合、そのウィンドウは、現在のアクティブな接続の資格情報によって開きます。 たとえば、CREATE DATABASE テンプレートを開くときに、オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde_md.md)] のインスタンスにフォーカスがあると、そのインスタンスへの接続を使用して新しいエディター ウィンドウが開きます。 アクティブな接続がない場合は、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] によってログイン ダイアログが表示されます。  
  
## <a name="see-also"></a>参照  
[[テンプレート エクスプローラー]](../../ssms/template/template-explorer.md)  
[[テンプレート パラメーターの値の指定]](../../ssms/template/replace-template-parameters.md)  
  
