---
title: allow updates サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 31
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 739b7aec3e30374fe16f700f6dcfc30bd763f024
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164352"
---
# <a name="allow-updates-server-configuration-option"></a>allow updates サーバー構成オプション
  このオプションは **sp_configure** ストアド プロシージャにまだ含まれていますが、その機能を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用することはできません。 設定しても何の影響もありません。 システム テーブルの直接更新はサポートされていません。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 **allow updates** オプションを変更すると、RECONFIGURE ステートメントが失敗します。 **allow updates** オプションへの変更は、すべてのスクリプトから削除する必要があります。  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  