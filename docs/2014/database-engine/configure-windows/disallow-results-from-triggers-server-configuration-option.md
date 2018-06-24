---
title: disallow results from triggers サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
caps.latest.revision: 28
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 482b544aa5609578d6310dfee849b404d31e1ac3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071001"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a>disallow results from triggers サーバー構成オプション
  **disallow results from triggers** オプションは、トリガーによって結果セットを返すかどうかを制御する場合に使用します。 結果セットを返すトリガーは、それと連動するように設計されていないアプリケーションでは予期しない動作を起こすことがあります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]この値は 1 に設定することをお勧めします。  
  
 1 に設定すると、 **disallow results from triggers** オプションが ON になります。 このオプションの既定値は 0 (OFF) です。 このオプションを 1 (ON) に設定した場合は、トリガーによって結果セットを返そうとするとエラーになり、次のエラー メッセージが出力されます。  
  
 "メッセージ 524、レベル 16、状態 1、プロシージャ \<プロシージャ名>、行 \<行番号>  
  
 "トリガーから結果セットが返されましたが、サーバー オプション 'disallow_results_from_triggers' は true です。"  
  
 **disallow results from triggers** オプションは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス レベルで適用され、インスタンス内のすべての既存のトリガーの動作を決定します。  
  
 **disallow results from triggers** は拡張オプションです。 **sp_configure** システム ストアド プロシージャを使用して disallow results from triggers の設定を変更するには、 **show advanced options** を 1 に設定する必要があります。 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
