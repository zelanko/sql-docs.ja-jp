---
title: "データ ソース ビューとデータ ソースへの変更の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6526be940f14de19cc6409dbb5fdbcdace701b46
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a>データ ソース ビューおよびデータ ソースへの変更の管理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]スキーマ生成ウィザードを再実行すると、ときに、同じデータ ソースと、元の生成に使用したデータ ソース ビューが再利用します。 データ ソースまたはデータ ソース ビューを追加しても、ウィザードでは使用されません。 最初の生成後に元のデータ ソースまたはデータ ソース ビューを削除した場合は、最初からウィザードを実行する必要があります。 ウィザードで以前使用した設定もすべて削除されます。 削除されたデータ ソースまたはデータ ソース ビューにバインドされていた、基になるデータベースの既存のオブジェクトは、次にスキーマ生成ウィザードを実行したとき、ユーザーが作成したオブジェクトとして取り扱われます。  
  
 データ ソース ビューに、基になるデータベースの生成時の実際の状態が反映されていないと、スキーマ生成ウィザードではサブジェクト領域データベースのスキーマを生成するときにエラーが発生する場合があります。 たとえば、データ ソース ビューで列のデータ型が **int**に指定されているときに、この列のデータ型が実際には **string**である場合、スキーマ生成ウィザードではデータ ソース ビューに合わせて外部キーのデータ型を **INT** に設定します。リレーションシップを作成すると、実際のデータ型が **string**であるため、処理は失敗します。  
  
 一方、データ ソース接続文字列を以前の生成後に別のデータベースに変更した場合は、エラーは発生しません。 この場合は新しいデータベースが使用され、以前のデータベースには変更は行われません。  
  
## <a name="see-also"></a>参照  
 [増分生成の理解](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)  
  
  
