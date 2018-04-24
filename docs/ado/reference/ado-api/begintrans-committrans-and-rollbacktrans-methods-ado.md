---
title: BeginTrans、CommitTrans、および RollbackTrans メソッド (ADO) |Microsoft ドキュメント
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
- Connection15::raw_RollbackTrans
- Connection15::CommitTrans
- Connection15::raw_CommitTrans
- Connection15::raw_BeginTrans
- Connection15::BeginTrans
- Connection15::RollbackTrans
helpviewer_keywords:
- BeginTrans method [ADO]
- CommitTrans method [ADO]
- RollbackTrans method [ADO]
ms.assetid: d4683472-4120-4236-8640-fa9ae289e23e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0d1f3a607ed6b39100b5de5c2d166bc428fbae7f
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>BeginTrans、CommitTrans、および RollbackTrans メソッド (ADO)
これらのトランザクション メソッド内のトランザクション処理の管理、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの次のようにします。  
  
-   **BeginTrans**新しいトランザクションを開始します。  
  
-   **CommitTrans**変更を保存し、現在のトランザクションを終了します。 新しいトランザクションを開始する場合もします。  
  
-   **RollbackTrans**現在のトランザクションで加えられた変更をキャンセルし、トランザクションを終了します。 新しいトランザクションを開始する場合もします。  
  
## <a name="syntax"></a>構文  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>戻り値  
 **BeginTrans**として返す関数を呼び出すことができます、**長い**トランザクションの入れ子レベルを示す変数。  
  
#### <a name="parameters"></a>パラメーター  
 *オブジェクト*  
 A**接続**オブジェクト。  
  
## <a name="connection"></a>接続  
 これらのメソッドを使用して、**接続**オブジェクトを保存または一連の 1 つの単位としてソース データに加えられた変更をキャンセルするとき。 たとえば、アカウント間でお金を振り替えるから金額を減算し、追加同じ量を他のします。 いずれかの更新が失敗した、口座の残高不要になった。 開いているトランザクション内でこれらの変更により、いずれかまたはすべての変更がを介して行われる。  
  
> [!NOTE]
>  すべてのプロバイダーは、トランザクションをサポートします。 いることを確認、プロバイダーによって定義されたプロパティ"**トランザクション DDL**"に表示されます、**接続**オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)プロバイダーをサポートしていることを示す、コレクショントランザクション。 プロバイダーがトランザクションをサポートしていない場合は、これらのメソッドのいずれかを呼び出すことはエラーを返します。  
  
 呼び出した後、 **BeginTrans**メソッド、プロバイダーが不要になった瞬時に変更がコミットが呼び出されるまで**CommitTrans**または**RollbackTrans**を終了しますトランザクションです。  
  
 呼び出し入れ子になったトランザクションをサポートするプロバイダのため、 **BeginTrans**開いているトランザクション内でメソッドが、新しい入れ子になったトランザクションを開始します。 戻り値は、入れ子のレベルを示します:「1」の戻り値は、最上位レベルのトランザクションを開いていることを示します (つまり、トランザクションは入れ子になっていない別のトランザクション内で)、「2」は、(第 2 レベルのトランザクションが開かれていることを示しますトランザクション内で入れ子に最上位レベルのトランザクション) などです。 呼び出す**CommitTrans**または**RollbackTrans**影響のみ、最後に開いたトランザクション以外の場合は、上位レベルのトランザクションを解決する前に、現在のトランザクションをロールバック閉じたりする必要があります。  
  
 呼び出す、 **CommitTrans**メソッドは、接続で開いているトランザクションで行われた変更を保存し、トランザクションを終了します。 呼び出す、 **RollbackTrans**メソッドは、開いているトランザクションで加えられた変更を反転し、トランザクションを終了します。 開かれたトランザクションが存在しない場合、いずれかのメソッドを呼び出すと、エラーが発生します。  
  
 によって、**接続**オブジェクトの[属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティのいずれかを呼び出す、 **CommitTrans**または**RollbackTrans**メソッド可能性があります新しいトランザクションを自動的に開始します。 場合、**属性**プロパティに設定されている**adXactCommitRetaining**、プロバイダーは、後に新しいトランザクションを自動的に開始、 **CommitTrans**呼び出します。 場合、**属性**プロパティに設定されている**adXactAbortRetaining**、プロバイダーは、後に新しいトランザクションを自動的に開始、 **RollbackTrans**呼び出します。  
  
## <a name="remote-data-service"></a>Remote Data Service  
 **BeginTrans**、 **CommitTrans**、および**RollbackTrans**メソッドでは使用できないクライアント側**接続**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [BeginTrans、CommitTrans、および RollbackTrans メソッドの例 (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [BeginTrans、CommitTrans、およびメソッドの例を示し (vc++)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Attributes プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
