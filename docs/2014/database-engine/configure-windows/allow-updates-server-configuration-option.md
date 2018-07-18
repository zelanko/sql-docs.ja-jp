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
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a9acdfa9668a49ed5e0c67a932bacc1ccee1ac6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196112"
---
# <a name="allow-updates-server-configuration-option"></a>allow updates サーバー構成オプション
  このオプションは **sp_configure** ストアド プロシージャにまだ含まれていますが、その機能を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用することはできません。 設定しても何の影響もありません。 システム テーブルの直接更新はサポートされていません。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 **allow updates** オプションを変更すると、RECONFIGURE ステートメントが失敗します。 **allow updates** オプションへの変更は、すべてのスクリプトから削除する必要があります。  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
