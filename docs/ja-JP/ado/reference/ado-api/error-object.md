---
title: オブジェクトのエラー |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error
helpviewer_keywords:
- error object [ADO]
ms.assetid: a175d453-fa55-4f49-9ede-a26d83177919
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa80ed69d629fe1c52853c57f6e491caa2864a85
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="error-object"></a>Error オブジェクト
プロバイダーを含む 1 つの操作に関連するデータ アクセス エラーの詳細が含まれています。  
  
## <a name="remarks"></a>解説  
 ADO オブジェクトに関連するすべての操作は、1 つまたは複数のプロバイダー エラーを生成できます。 各エラーが発生すると、1 つまたは複数**エラー**でオブジェクトを配置している、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)のコレクション、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。 ADO の別の操作が、エラーを生成するときに、**エラー**コレクションをクリアすると、および一連の新しい**エラー**でオブジェクトを配置、**エラー**コレクション。  
  
> [!NOTE]
>  各**エラー**オブジェクトは ADO エラーではなく、特定のプロバイダー エラーを表します。 ADO エラーは、実行時の例外処理機構に公開されます。 たとえば、Microsoft Visual Basic では、ADO 固有エラーの発生がトリガー、 **On Error**イベントに表示されると、**エラー**オブジェクト。 ADO エラーの一覧については、次を参照してください。、 [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)トピックです。  
  
 読み取ることができます、**エラー**オブジェクトのプロパティを取得して、次を含む、各エラーに関する特定の詳細。  
  
-   [説明](../../../ado/reference/ado-api/description-property.md)プロパティで、エラーのテキストが含まれています。 これは、既定のプロパティです。  
  
-   [数](../../../ado/reference/ado-api/number-property-ado.md)プロパティが含まれていますが、**長い**エラー定数の整数値。  
  
-   [ソース](../../../ado/reference/ado-api/source-property-ado-error.md)プロパティで、エラーが発生したオブジェクトを識別します。 これは、いくつかがある場合に特に便利です**エラー**内のオブジェクト、**エラー**コレクションの次のデータ ソースに要求します。  
  
-   [SQLState](../../../ado/reference/ado-api/sqlstate-property.md)と[以下](../../../ado/reference/ado-api/nativeerror-property-ado.md)プロパティで、SQL データ ソースから情報を入力します。  
  
 配置されているプロバイダーのエラーが発生したときに、**エラー**のコレクション、**接続**オブジェクト。 ADO では、プロバイダーに固有のエラー情報を許可する 1 つの ADO 操作で複数のエラーの戻り値をサポートします。 エラー ハンドラーには、この詳細なエラー情報を入手するには、言語、または使用している環境の適切なエラー トラッピング機能を使用してそれぞれのプロパティを列挙する入れ子になったループを使用して**エラー**オブジェクトには**エラー**コレクション。  
  
> [!NOTE]
>  **Microsoft Visual Basic と VBScript ユーザー**が有効な場合**接続**オブジェクト、エラー情報を取得する必要があります、**エラー**オブジェクト。  
  
 プロバイダーと同様には、ADO をクリア、 **OLE エラー Info**オブジェクトの呼び出しを行う可能性があります、新しいプロバイダー エラーを生成可能性のある前にします。 ただし、**エラー**コレクションに、**接続**オブジェクトはオフであり、プロバイダーが、新しいエラーを生成するときにのみ、または、[クリア](../../../ado/reference/ado-api/clear-method-ado.md)メソッドが呼び出されます。  
  
 プロパティとメソッドの一部として表示される警告を返します**エラー**内のオブジェクト、**エラー**コレクションが、プログラムの実行を停止しないでください。 呼び出す前に、[再同期](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドを[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト;、 [を開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドを**接続**; オブジェクトまたは設定、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティを**Recordset**オブジェクトを呼び出す、 **をオフに**メソッドを**エラー**コレクション。 読み取ることができるように、[カウント](../../../ado/reference/ado-api/count-property-ado.md)のプロパティ、**エラー**コレクションをテストするには、警告が返されました。  
  
 **エラー**オブジェクトはスクリプトを実行しても安全ではありません。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [Error オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
