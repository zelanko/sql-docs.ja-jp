---
title: "イミディ エイト モード |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], immediate mode
- immediate mode [ADO]
- updating data [ADO], immediate mode
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 072e6f71aca74f4690f26b90887d475a955e3041
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="immediate-mode"></a>イミディ エイト モード
イミディ エイト モードが有効になってときに、 **LockType**プロパティに設定されている**adLockOptimistic**または**adLockPessimistic**です。 操作を宣言する行の完了を呼び出してとすぐには、レコードに対する変更をデータ ソースに反映するようイミディ エイト モードで、**更新**メソッドです。  
  
## <a name="calling-update"></a>Update を呼び出す  
 レコードから移動した場合の追加または編集する呼び出しの前に、**更新**メソッド、ADO は自動的に呼び出す**更新**変更を保存します。 呼び出す必要があります、**ただし**ナビゲーション、現在のレコードに加えられた変更を取り消すか、新しく追加されたレコードを破棄する場合よりも先メソッドです。  
  
 現在のレコードを呼び出した後、**更新**メソッドです。  
  
## <a name="cancelupdate"></a>ただし  
 使用して、**ただし**メソッドを現在の行に加えられた変更を取り消すまたは新しく追加した行を破棄します。 呼び出した後は、現在の行、または新しい行への変更を取り消すことはできません、**更新**メソッドを変更することができますをロールバックすると、トランザクションの一部である場合を除き、 **RollbackTrans**メソッドの全体または一部バッチ更新します。 バッチ更新をキャンセルできます、**更新**で、**ただし**または**CancelBatch**メソッドです。  
  
 呼び出すと、新しい行を追加しているかどうか、**ただし**メソッド、現在の行が前に、の現在の行、 **AddNew**呼び出します。  
  
 現在の行の変更や、新しい行の追加はありません場合、呼び出し元、**ただし**メソッドには、エラーが生成されます。

