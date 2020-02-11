---
title: BeginTrans、CommitTrans、および RollbackTrans メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c3a8bc22e57d91ab64bdbbc5fc694575a8aa8ff9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920523"
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>BeginTrans、CommitTrans、および RollbackTrans メソッド (ADO)
これらのトランザクションメソッドは、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト内のトランザクション処理を次のように管理します。  
  
-   **BeginTrans**新しいトランザクションを開始します。  
  
-   **CommitTrans**すべての変更を保存し、現在のトランザクションを終了します。 また、新しいトランザクションを開始することもできます。  
  
-   **RollbackTrans**現在のトランザクション中に行われたすべての変更をキャンセルし、トランザクションを終了します。 また、新しいトランザクションを開始することもできます。  
  
## <a name="syntax"></a>構文  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>戻り値  
 **BeginTrans**は、トランザクションの入れ子レベルを示す**長い**変数を返す関数として呼び出すことができます。  
  
#### <a name="parameters"></a>パラメーター  
 *素材*  
 **接続**オブジェクトです。  
  
## <a name="connection"></a>接続  
 ソースデータに対して行われた一連の変更を1つの単位として保存またはキャンセルする場合は、これらのメソッドを**接続**オブジェクトと共に使用します。 たとえば、勘定科目間で通貨を転送する場合は、1つから金額を減算し、同じ金額をもう一方に追加します。 どちらかの更新が失敗した場合、アカウントの残高はなくなります。 開いているトランザクション内でこれらの変更を行うことによって、すべての変更が行われないようにすることができます。  
  
> [!NOTE]
>  すべてのプロバイダーがトランザクションをサポートするわけではありません。 プロバイダーがトランザクションをサポートしていることを示す、プロバイダー定義プロパティ "**TRANSACTION DDL**" が**接続**オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションに表示されていることを確認します。 プロバイダーがトランザクションをサポートしていない場合、これらのメソッドのいずれかを呼び出すと、エラーが返されます。  
  
 **BeginTrans**メソッドを呼び出した後、このプロバイダーは、 **CommitTrans**または**RollbackTrans**を呼び出してトランザクションを終了するまで、加えた変更を即座にコミットしなくなります。  
  
 入れ子になったトランザクションをサポートするプロバイダーの場合、開いているトランザクション内で**BeginTrans**メソッドを呼び出すと、新しい入れ子になったトランザクションが開始されます。 戻り値は、入れ子のレベルを示します。戻り値 "1" は、最上位レベルのトランザクションを開いている (つまり、トランザクションが別のトランザクション内で入れ子になっていない) ことを示します。 "2" は、第2レベルのトランザクションを開いたことを示します (トランザクションは最上位レベルのトランザクション内に入れ子になっています)。 **CommitTrans**または**RollbackTrans**を呼び出すと、最後に開かれたトランザクションのみに影響します。上位レベルのトランザクションを解決する前に、現在のトランザクションを閉じるかロールバックする必要があります。  
  
 **CommitTrans**メソッドを呼び出すと、接続時に開いているトランザクション内で行われた変更が保存され、トランザクションが終了します。 **RollbackTrans**メソッドを呼び出すと、開いているトランザクション内で行われたすべての変更が元に戻され、トランザクションが終了します。 開いているトランザクションが存在しないときにいずれかのメソッドを呼び出すと、エラーが生成されます。  
  
 **接続**オブジェクトの[Attributes](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティによっては、 **CommitTrans**メソッドまたは**RollbackTrans**メソッドを呼び出すと、新しいトランザクションが自動的に開始される場合があります。 **Attributes**プロパティが**adXactCommitRetaining**に設定されている場合、プロバイダーは、 **CommitTrans**呼び出しの後に新しいトランザクションを自動的に開始します。 **Attributes**プロパティが**Adxactabortretaining**に設定されている場合、プロバイダーは、呼び出しの後**** に新しいトランザクションを自動的に開始します。  
  
## <a name="remote-data-service"></a>リモートデータサービス  
 クライアント側の**接続**オブジェクトでは、 **BeginTrans**、 **CommitTrans**、および**RollbackTrans**の各メソッドは使用できません。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [BeginTrans、CommitTrans、および RollbackTrans メソッドの例 (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [BeginTrans、CommitTrans、および RollbackTrans メソッドの例 (VC + +)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Attributes プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
