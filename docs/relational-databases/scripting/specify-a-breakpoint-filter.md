---
title: ブレークポイント フィルターの指定 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 40cd627b8c8a90f43d9ee9cee53f85a5c5b65782
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="specify-a-breakpoint-filter"></a>ブレークポイント フィルターの指定
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
  
