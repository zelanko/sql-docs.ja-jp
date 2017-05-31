---
title: "ブレークポイント フィルターの指定 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 52893c5409981b492e10ff1706def0257367c494
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="specify-a-breakpoint-filter"></a>ブレークポイント フィルターの指定
  ブレークポイント フィルターは、ブレークポイントが指定したコンピューター、オペレーティング システム プロセス、およびスレッドだけで動作するように制限します。 通常、ブレークポイント フィルターは、並列アプリケーションをデバッグするときに使用されます。  
  
##  <a name="BKMK_ActionConsiderations"></a> フィルターに関する注意点  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトおよびストアド プロシージャは並列アプリケーションではないため、ブレークポイント フィルターは [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは通常使用されません。  
  
#### <a name="to-specify-a-breakpoint-filter"></a>ブレークポイント フィルターを指定するには  
  
1.  エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[フィルター]** をクリックします。  
  
     - または -  
  
     **[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[フィルター]** をクリックします。  
  
2.  **[ブレークポイント フィルター]** ダイアログ ボックスで、 **[フィルター]** ボックスを使用して、コンピューター名を指定するか、またはオペレーティング システム プロセスとスレッドを名前または ID 番号で指定します。  
  
    -   **MachineName** は、データベース エンジンのインスタンスを実行しているコンピューターです。  
  
    -   **ProcessID**および **ProcessName** は、データベース エンジンのインスタンスを実行しているオペレーティング システム プロセスです。  
  
    -   **ThreadID** および **ThreadName** は、データベース エンジンのインスタンス内で [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ、プロシージャ、または関数を実行しているオペレーティング システム スレッドです。  
  
3.  **[OK]** をクリックして変更を適用するか、 **[キャンセル]** をクリックして変更を適用せずに終了します。  
  
## <a name="see-also"></a>参照  
 [ブレークポイント条件の指定](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [ヒット カウントの指定](../../relational-databases/scripting/specify-a-hit-count.md)   
 [ブレークポイント アクションの指定](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
