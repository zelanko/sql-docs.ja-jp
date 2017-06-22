---
title: "[スレッド] ウィンドウ | Microsoft Docs"
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
- vs.debug.threads
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c5b7d3f057bddab388a75ad48f447ede194c8aa0
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="transact-sql-debugger---threads-window"></a>Transact-SQL デバッガー - [スレッド] ウィンドウ
  **[スレッド]** ウィンドウには、デバッグ中の [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター セッションで使用されている [!INCLUDE[ssDE](../../includes/ssde-md.md)] スレッドに関する情報が表示されます。 スレッドの情報を表示するには、デバッグ モードである必要があります。  
  
## <a name="task-list"></a>タスク一覧  
 **[スレッド] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[ウィンドウ]**をポイントし、 **[スレッド]**をクリックします。  
  
## <a name="columns"></a>列  
 **ID**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーがスレッドに割り当てる一意な識別番号。 スレッドの詳細情報を参照するには、sys.dm_os_threads 動的管理ビューから行を選択します。  
  
 簡易プーリング モードで実行していない場合は、os_thread_id の値が **[ID]** 列の値に一致する行を選択します。 簡易プーリング モードで実行している場合は、fiber_context_address の値が **[ID]** 列の値に一致する行を選択します。  
  
 **名前**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] セッションの情報を **ComputerName/InstanceName [SPID]**の形式で表示します。  
  
 **[ComputerName]**  
 クエリ エディター セッションが接続している [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを実行しているコンピューターの名前。  
  
 **InstanceName**  
 クエリ エディター セッションが接続している [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスの名前。  
  
 **[SPID]**  
 このセッションを一意に識別する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセッション プロセス ID。 セッションの詳細情報を参照するには、spid 列と同じ値を持つ sys.sysprocesses ビューの行を選択します。  
  
 **場所**  
 デバッグ中のクエリ エディター セッションで使用されているスクリプト ファイルの名前を表示します。  
  
 **[Priority]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーはこの機能をサポートしていません。  
  
 **[中断]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーはこの機能をサポートしていません。  
  
## <a name="see-also"></a>参照  
 [Transact-SQL デバッガー](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Transact-SQL デバッガー情報](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)  
  
  
