---
title: "トランザクション処理 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ADO]
- data updates [ADO], transaction processing
- updating data [ADO], transaction processing
- nested transactions [ADO]
ms.assetid: 74ab6706-e2dc-42cb-af77-dbc58a9cf4ce
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a2afb43e83ebc2ed765c04fa15f070597009457
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="transaction-processing"></a>トランザクション処理
A*トランザクション*の先頭と末尾の一連のデータ アクセス操作の間の接続で実行を区切ります。 データ ソースのトランザクション機能により制限、**接続**オブジェクトでは作成し、トランザクションを管理することもできます。 たとえば、Microsoft SQL Server 上のデータベースにアクセスする、Microsoft OLE DB Provider for SQL Server を使用して、トランザクションを作成できます複数入れ子になったを実行するコマンドをします。  
  
 ADO では、トランザクションでの操作によってデータ ソースへの変更が正常に実行されないかを実行することです。  
  
 トランザクションをキャンセルした場合、またはその操作のいずれかが失敗した場合は、結果は、トランザクション内の操作のいずれも発生したかのようになります。 データ ソースは、トランザクションの開始前に残ります。  
  
 ADO には、トランザクションを制御する以下の方法が用意されています: **BeginTrans**、 **CommitTrans**、および**RollbackTrans**です。 これらのメソッドを使用して、**接続**オブジェクトを保存または一連の 1 つの単位としてソース データに加えられた変更をキャンセルするとき。 たとえば、アカウント間でお金を振り替えるから金額を減算し、追加同じ量を他のします。 いずれかの更新が失敗した、口座の残高不要になった。 開いているトランザクション内でこれらの変更により、いずれかまたはすべての変更がを介して行われる。  
  
> [!NOTE]
>  すべてのプロバイダーは、トランザクションをサポートします。 いることを確認、プロバイダーによって定義されたプロパティ"**トランザクション DDL**"に表示されます、**接続**オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)プロバイダーをサポートしていることを示す、コレクショントランザクション。 プロバイダーがトランザクションをサポートしていない場合は、これらのメソッドのいずれかを呼び出すことはエラーを返します。  
  
 呼び出した後、 **BeginTrans**メソッド、プロバイダーが不要になった瞬時に変更がコミットが呼び出されるまで**CommitTrans**または**RollbackTrans**を終了しますトランザクションです。  
  
 呼び出す、 **CommitTrans**メソッドは、接続で開いているトランザクションで行われた変更を保存し、トランザクションを終了します。 呼び出す、 **RollbackTrans**メソッドは、開いているトランザクションで加えられた変更を反転し、トランザクションを終了します。 開かれたトランザクションが存在しない場合、いずれかのメソッドを呼び出すと、エラーが発生します。  
  
 によって、**接続**オブジェクトの[属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティのいずれかを呼び出す、 **CommitTrans**または**RollbackTrans**メソッド可能性があります新しいトランザクションを自動的に開始します。 場合、**属性**プロパティに設定されている**adXactCommitRetaining**、プロバイダーは、後に新しいトランザクションを自動的に開始、 **CommitTrans**呼び出します。 場合、**属性**プロパティに設定されている**adXactAbortRetaining**、プロバイダーは、後に新しいトランザクションを自動的に開始、 **RollbackTrans**呼び出します。  
  
## <a name="transaction-isolation-level"></a>トランザクション分離レベル  
 使用して、 **IsolationLevel**でトランザクションの分離レベルを設定するプロパティ、**接続**オブジェクト。 この設定は反映されません次回を呼び出すまで、 [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)メソッドです。 要求した分離レベルが使用できない場合、プロバイダーは、次に高い分離レベルを返す可能性があります。 参照してください、 **IsolationLevel**有効な値の詳細については、ADO プログラマのリファレンス内のプロパティです。  
  
## <a name="nested-transactions"></a>入れ子になったトランザクション  
 呼び出し入れ子になったトランザクションをサポートするプロバイダのため、 **BeginTrans**開いているトランザクション内でメソッドが、新しい入れ子になったトランザクションを開始します。 戻り値は、入れ子のレベルを示します:「1」の戻り値は、最上位レベルのトランザクションを開いていることを示します (つまり、トランザクションは入れ子になっていない別のトランザクション内で)、「2」は、(第 2 レベルのトランザクションが開かれていることを示しますトランザクション内で入れ子に最上位レベルのトランザクション) などです。 呼び出す**CommitTrans**または**RollbackTrans**影響のみ、最後に開いたトランザクション以外の場合は、上位レベルのトランザクションを解決する前に、現在のトランザクションをロールバック閉じたりする必要があります。
