---
title: データ ソース ビューとデータ ソースへの変更の管理 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f8cb72fe4650cd76465207f3e7cd529e2a7b032
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a>データ ソース ビューおよびデータ ソースへの変更の管理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  スキーマ生成ウィザードが再実行されると、元の生成に使用されたものと同じデータ ソースとデータ ソース ビューが再び使用されます。 データ ソースまたはデータ ソース ビューを追加しても、ウィザードでは使用されません。 最初の生成後に元のデータ ソースまたはデータ ソース ビューを削除した場合は、最初からウィザードを実行する必要があります。 ウィザードで以前使用した設定もすべて削除されます。 削除されたデータ ソースまたはデータ ソース ビューにバインドされていた、基になるデータベースの既存のオブジェクトは、次にスキーマ生成ウィザードを実行したとき、ユーザーが作成したオブジェクトとして取り扱われます。  
  
 データ ソース ビューに、基になるデータベースの生成時の実際の状態が反映されていないと、スキーマ生成ウィザードではサブジェクト領域データベースのスキーマを生成するときにエラーが発生する場合があります。 たとえば、データ ソース ビューで列のデータ型が **int**に指定されているときに、この列のデータ型が実際には **string**である場合、スキーマ生成ウィザードではデータ ソース ビューに合わせて外部キーのデータ型を **INT** に設定します。リレーションシップを作成すると、実際のデータ型が **string**であるため、処理は失敗します。  
  
 一方、データ ソース接続文字列を以前の生成後に別のデータベースに変更した場合は、エラーは発生しません。 この場合は新しいデータベースが使用され、以前のデータベースには変更は行われません。  
  
## <a name="see-also"></a>参照  
 [増分生成の理解](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)  
  
  
