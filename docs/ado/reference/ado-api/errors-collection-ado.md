---
title: "Errors コレクション (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::Errors
- Connection15::get_Errors
- Connection15::GetErrors
helpviewer_keywords:
- Errors collection [ADO]
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 27ca46528314f34b769d505269ade0c73fb1b051
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="errors-collection-ado"></a>Errors コレクション (ADO)
すべてが含まれています、[エラー](../../../ado/reference/ado-api/error-object.md) 1 つのプロバイダーに関連する障害への応答で作成されたオブジェクト。  
  
## <a name="remarks"></a>解説  
 ADO オブジェクトに関連するすべての操作は、1 つまたは複数のプロバイダー エラーを生成できます。 各エラーが発生すると、1 つまたは複数**エラー**にオブジェクトを配置することができます、**エラー**のコレクション、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。 ADO の別の操作が、エラーを生成するときに、**エラー** 、コレクションをクリアし、一連の新しい**エラー**にオブジェクトを配置することができます、**エラー**コレクション。  
  
 各**エラー**オブジェクトは ADO エラーではなく、特定のプロバイダー エラーを表します。 ADO エラーは、実行時の例外処理機構に公開されます。 たとえば、Microsoft Visual Basic では、ADO 固有エラーの発生がトリガー、 [onError](../../../ado/reference/rds-api/onerror-event-rds.md)イベントに表示されると、 **Err**オブジェクト。  
  
 エラーを生成しない ADO 操作がある影響しない、**エラー**コレクション。 使用して、[オフ](../../../ado/reference/ado-api/clear-method-ado.md)を手動で消去する方法、**エラー**コレクション。  
  
 一連の**エラー**内のオブジェクト、**エラー**コレクションで 1 つのステートメントへの応答で発生したすべてのエラーについて説明します。 特定のエラーを列挙する、**エラー**コレクションにより、エラー処理ルーチンより正確に原因と、エラーの発生元を確認し、適切な回復手順を実行します。  
  
 プロパティとメソッドの一部として表示される警告を返します**エラー**内のオブジェクト、**エラー**コレクションが、プログラムの実行を停止しないでください。 呼び出す前に、[再同期](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)のメソッド、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、 [を開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドを**接続**オブジェクト、または設定、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティを**Recordset**オブジェクトを呼び出す、 **をオフに**メソッドを**エラー**コレクション。 読み取ることができるように、[カウント](../../../ado/reference/ado-api/count-property-ado.md)のプロパティ、**エラー**コレクションをテストするには、警告が返されました。  
  
> [!NOTE]
>  参照してください、**エラー**オブジェクトの 1 つの ADO 操作が複数のエラーを生成する方法の詳細な説明のトピックです。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [Errors コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)   
 [付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
