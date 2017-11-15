---
title: "allow updates サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cbf1454658cc74e2b4bd1c6bf44acdd7c2b25ad
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="allow-updates-server-configuration-option"></a>allow updates サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このオプションは **sp_configure** ストアド プロシージャにまだ含まれていますが、その機能を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用することはできません。 設定しても何の影響もありません。 システム テーブルの直接更新はサポートされていません。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 **allow updates** オプションを変更すると、RECONFIGURE ステートメントが失敗します。 **allow updates** オプションへの変更は、すべてのスクリプトから削除する必要があります。  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
