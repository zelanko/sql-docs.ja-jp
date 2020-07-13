---
title: '[スレッド] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f3460c892c182996a753c2a16076418a6b2008f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063328"
---
# <a name="threads-window"></a>[スレッド] ウィンドウ
  **[スレッド]** ウィンドウには、デバッグ中の [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター セッションで使用されている [!INCLUDE[ssDE](../../includes/ssde-md.md)] スレッドに関する情報が表示されます。 スレッドの情報を表示するには、デバッグ モードである必要があります。  
  
## <a name="task-list"></a>タスク一覧  
 **[スレッド] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[ウィンドウ]** をポイントし、 **[スレッド]** をクリックします。  
  
## <a name="columns"></a>[列]  
 **ID**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーがスレッドに割り当てる一意な識別番号。 スレッドの詳細情報を参照するには、sys.dm_os_threads 動的管理ビューから行を選択します。  
  
 簡易プーリング モードで実行していない場合は、os_thread_id の値が **[ID]** 列の値に一致する行を選択します。 簡易プーリング モードで実行している場合は、fiber_context_address の値が **[ID]** 列の値に一致する行を選択します。  
  
 **Name**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] セッションの情報を **ComputerName/InstanceName [SPID]** の形式で表示します。  
  
 **[ComputerName]**  
 クエリ エディター セッションが接続している [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを実行しているコンピューターの名前。  
  
 **InstanceName**  
 クエリ エディター セッションが接続している [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスの名前。  
  
 **[SPID]**  
 このセッションを一意に識別する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセッション プロセス ID。 セッションの詳細情報を参照するには、spid 列と同じ値を持つ sys.sysprocesses ビューの行を選択します。  
  
 **Location**  
 デバッグ中のクエリ エディター セッションで使用されているスクリプト ファイルの名前を表示します。  
  
 **優先順位**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーはこの機能をサポートしていません。  
  
 **[中断]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーはこの機能をサポートしていません。  
  
## <a name="see-also"></a>参照  
 [Transact-SQL デバッガー](transact-sql-debugger.md)   
 [Transact-SQL デバッガー情報](transact-sql-debugger-information.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  
