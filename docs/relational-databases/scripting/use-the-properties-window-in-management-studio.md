---
title: Management Studio の [プロパティ] ウィンドウの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7721c6fddd9a17f5edaee817810de1b91dcc1c7a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635900"
---
# <a name="use-the-properties-window-in-management-studio"></a>Management Studio の [プロパティ] ウィンドウの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [プロパティ] ウィンドウには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]内の項目 (接続、プラン表示操作など) の状態や、データベース オブジェクト (テーブル、ビュー、デザイナーなど) の情報が表示されます。  
  
 [プロパティ] ウィンドウを使用して、現在の接続のプロパティを表示できます。 [プロパティ] ウィンドウに表示される多くのプロパティは読み取り専用ですが、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]内の別の場所で変更できます。 たとえば、[プロパティ] ウィンドウに表示されるクエリの [データベース] プロパティは読み取り専用ですが、ツール バーからの変更が可能です。  
  
### <a name="to-view-properties-using-the-properties-window"></a>[プロパティ] ウィンドウを使用してプロパティを表示するには  
  
1.  [プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。  
  
2.  表示するオブジェクトにフォーカスを設定します。  
  
3.  [プロパティ] ウィンドウで特定のプロパティを探します。  
  
### <a name="to-view-connection-properties-of-a-query-window"></a>クエリ ウィンドウの接続プロパティを表示するには  
  
1.  [プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。  
  
2.  [プロパティ] ウィンドウですべての接続プロパティを確認できます。  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a>プラン表示操作のプロパティを表示するには  
  
1.  **[クエリ]** メニューの **[実際の実行プランを含める]** をクリックします。  
  
2.  SQL クエリ エディターで、クエリを入力して実行します。  
  
3.  [プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。  
  
4.  SQL クエリ エディターの **[実行プラン]** タブでオペレーターのアイコンをクリックすると、[プロパティ] ウィンドウにそのオペレーターの情報が表示されます。  
  
## <a name="see-also"></a>参照  
 [[プロパティ] ウィンドウ &#40;Management Studio&#41;](http://msdn.microsoft.com/library/6a9a1389-df8d-4cfc-928b-eccbf884a22d)  
  
  
