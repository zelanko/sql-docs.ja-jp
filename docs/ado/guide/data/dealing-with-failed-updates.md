---
description: 失敗した更新の処理
title: 失敗した更新プログラムの処理 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
author: rothja
ms.author: jroth
ms.openlocfilehash: 508508da57fc7a0b1ab899acf3f77b1a49a7fa9b
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806929"
---
# <a name="dealing-with-failed-updates"></a>失敗した更新の処理
更新がエラーで終了した場合、エラーの解決方法は、エラーの性質と重大度、およびアプリケーションのロジックによって異なります。 ただし、データベースが他のユーザーと共有されている場合、一般的なエラーとして、他のユーザーがフィールドを変更することがあります。 この種類のエラーは競合と呼ばれます。 ADO はこの状況を検出し、エラーを報告します。  
  
## <a name="remarks"></a>コメント  
 更新エラーが発生した場合は、エラー処理ルーチンでトラップされます。 競合する行だけが表示されるように、Adfilter衝突 Tingrecords 定数でレコードセットをフィルター処理します。 この例では、エラー解決方法は、作成者の姓と名 (au_fname と au_lname) を出力するだけです。  
  
 更新の競合についてユーザーに通知するコードは、次のようになります。  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>参照  
 [バッチ モード](./batch-mode.md)