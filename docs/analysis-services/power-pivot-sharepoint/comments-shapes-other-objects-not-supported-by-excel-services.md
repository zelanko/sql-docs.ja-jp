---
title: "コメント、図形、Excel Services によってサポートされていないその他のオブジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e81433f28d9b3b3f20ceb99f2e6436a689ba4e86
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="comments-shapes-other-objects-not-supported-by-excel-services"></a>コメント、図形、Excel Services によってサポートされていないその他のオブジェクト
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
このエラーは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] フィールドの一覧から [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにスライサーを追加すると発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Excel Web Access では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] フィールドの一覧からブックに追加されたスライサーの位置指定および書式設定の制御に使用される図形オブジェクトを表示することができません。|  
|メッセージ テキスト|次の機能は Excel Services でサポートされておらず、表示されないか、一部しか表示されないことがあります。<br /><br /> コメント、図形、またはその他のオブジェクト<br /><br /> 外部データのクエリなど、一部の機能では、Microsoft Excel でのみ更新できるキャッシュ データが表示されます。|  
  
## <a name="explanation"></a>説明  
 Excel Web Access では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをブラウザーで開き、 **"サポートされていない機能 このブックは意図されたようには表示されない可能性があります"** というメッセージの **[詳細]**ボタンをクリックすると、このエラーが表示されます。  
  
 このエラーは、Excel の非表示の図形オブジェクトによって制御されるレイアウトを持つスライサーが [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにある場合に発生します。 図形オブジェクトは、水平配置と垂直配置におけるスライサーの書式設定および位置指定を制御します。  
  
 Excel Services では図形オブジェクトを表示できませんが、このオブジェクトは非表示であるので、表示できないことは問題ではありません。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーは無視してかまいません。 **[OK]** をクリックして、エラー メッセージを閉じ、ブックとスライサーの使用を問題なく続けることができます。  
  
  
