---
title: データ ソース ビュー (Analysis Services) の削除 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9e4467d476acbb45e0ec18c7a28fd1a9a143c386
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178573"
---
# <a name="delete-a-data-source-view-analysis-services"></a>データ ソース ビューの削除 (Analysis Services)
  OLAP プロジェクトでデータ ソース ビュー (DSV) を使用していない場合、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でプロジェクトから DSV を削除できます。  
  
 DSV は、削除すると完全に失われます。 削除した DSV を、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のプロジェクトまたはデータベースに復元することはできません。  
  
 他のオブジェクトが依存している DSV は、オンライン モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって開かれた [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] データベースから削除できません。 サーバーで実行中のデータベースに接続されているプロジェクトから DSV を削除するには、DSV 自体を削除する前に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内でその DSV に依存しているすべてのオブジェクトを削除する必要があります。  
  
 DSV を削除すると、依存している他の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが無効になります。そのため、DSV を削除する前に、DSV を削除すると無効になるオブジェクトの一覧が表示されます。 使用する予定のあるオブジェクトが含まれていないか、この一覧で確認します。  
  
 ![オブジェクトのダイアログ ボックスを削除](../media/ssas-olapdsv-deleteobjects.gif "オブジェクトの削除 ダイアログ ボックス")  
  
## <a name="see-also"></a>参照  
 [多次元モデル内のデータ ソース ビュー](data-source-views-in-multidimensional-models.md)   
 [データ ソース ビューでプロパティを変更&#40;Analysis Services&#41;](change-properties-in-a-data-source-view-analysis-services.md)  
  
  