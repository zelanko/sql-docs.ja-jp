---
title: "Management Studio の [プロパティ] ウィンドウの使用 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: adef30d9bc7488bc56c3d118962028b4b005c2fa
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="use-the-properties-window-in-management-studio"></a>Management Studio の [プロパティ] ウィンドウの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] プロパティ ウィンドウには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 内の項目 (接続、プラン表示操作など) の状態や、データベース オブジェクト (テーブル、ビュー、デザイナーなど) の情報が表示されます。  
  
 [プロパティ] ウィンドウを使用して、現在の接続のプロパティを表示できます。 [プロパティ] ウィンドウに表示される多くのプロパティは読み取り専用ですが、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]内の別の場所で変更できます。 たとえば、[プロパティ] ウィンドウに表示されるクエリの [データベース] プロパティは読み取り専用ですが、ツール バーからの変更が可能です。  
  
### <a name="to-view-properties-using-the-properties-window"></a>[プロパティ] ウィンドウを使用してプロパティを表示するには  
  
1.  [プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。  
  
2.  表示するオブジェクトにフォーカスを設定します。  
  
3.  [プロパティ] ウィンドウで特定のプロパティを探します。  
  
### <a name="to-view-connection-properties-of-a-query-window"></a>クエリ ウィンドウの接続プロパティを表示するには  
  
1.  [プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。  
  
2.  [プロパティ] ウィンドウですべての接続プロパティを確認できます。  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a>プラン表示操作のプロパティを表示するには  
  
1.  **[クエリ]** メニューの **[実際の実行プランを含める]**をクリックします。  
  
2.  SQL クエリ エディターで、クエリを入力して実行します。  
  
3.  [プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。  
  
4.  SQL クエリ エディターの **[実行プラン]** タブでオペレーターのアイコンをクリックすると、[プロパティ] ウィンドウにそのオペレーターの情報が表示されます。  
  
## <a name="see-also"></a>参照  
 [[プロパティ] ウィンドウ &#40;Management Studio&#41;](http://msdn.microsoft.com/library/6a9a1389-df8d-4cfc-928b-eccbf884a22d)  
  
  
