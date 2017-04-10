---
title: "disallow results from triggers サーバー構成オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "トリガー [SQL Server], 結果セット"
  - "結果セット [SQL Server], トリガー"
  - "disallow results from triggers オプション"
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# disallow results from triggers サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **disallow results from triggers** オプションは、トリガーによって結果セットを返すかどうかを制御する場合に使用します。 結果セットを返すトリガーは、それと連動するように設計されていないアプリケーションでは予期しない動作を起こすことがあります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] この値は 1 に設定することをお勧めします。  
  
 1 に設定すると、**disallow results from triggers** オプションが ON になります。 このオプションの既定値は 0 (OFF) です。 このオプションを 1 (ON) に設定した場合は、トリガーによって結果セットを返そうとするとエラーになり、次のエラー メッセージが出力されます。  
  
 "メッセージ 524、レベル 16、状態 1、プロシージャ \<プロシージャ名>、行 \<行番号>  
  
 "トリガーから結果セットが返されましたが、サーバー オプション 'disallow_results_from_triggers' は true です。"  
  
 **disallow results from triggers** オプションは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス レベルで適用され、インスタンス内のすべての既存のトリガーの動作を決定します。  
  
 **disallow results from triggers** は拡張オプションです。 **sp_configure** システム ストアド プロシージャを使用して disallow results from triggers の設定を変更するには、**show advanced options** を 1 に設定する必要があります。 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## 参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  