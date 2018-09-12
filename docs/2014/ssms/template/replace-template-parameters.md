---
title: テンプレート パラメーターを置き換える | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 04ec0872a0a0daf82ca54107a7f60639cd1ed9d9
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818498"
---
# <a name="replace-template-parameters"></a>[テンプレート パラメーターの置換]
  テンプレートには、テンプレートを使用するたびに実装固有の値に置き換えることができるパラメーターが含まれています。 コード エディターでテンプレートを開いた後、パラメーターを実装に関する値に置き換えることができます。  
  
## <a name="before-you-begin"></a>はじめに  
 **[テンプレート パラメーターの値の指定]** ダイアログは、3 つの列を含むグリッドです。 **[パラメーター]** 列と **[種類]** 列は読み取り専用であり、変更できません。 **[値]** 列の内容を確認し、既定値を実装に応じた値に変更します。  
  
 このダイアログ ボックスを使用するには、スクリプトに山かっこ (`< >`) で囲んだパラメーターを `<`*parameter_name*`,` *data_type*`,` *default_value*`>`の形式で含める必要があります。  
  
## <a name="replace-template-parameters"></a>[テンプレート パラメーターの置換]  
 コード エディター ウィンドウでテンプレートを開いた後、次の操作を行います。  
  
1.  **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。  
  
2.  **[テンプレート パラメーターの値の指定]** ダイアログ ボックスの **[値]** 列には、各パラメーターの推奨値が表示されます。 推奨値をそのまま使用するか、または別の値を入力します。  
  
3.  **[OK]** をクリックして **[テンプレート パラメーターを置き換える]** ダイアログ ボックスを閉じ、クエリ エディターでスクリプトを変更します。  
  
## <a name="see-also"></a>参照  
 [テンプレート エクスプ ローラー](template-explorer.md)   
 [テンプレートを開く](open-a-template.md)  
  
  
