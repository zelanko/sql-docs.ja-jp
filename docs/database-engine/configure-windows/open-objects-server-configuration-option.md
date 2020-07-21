---
title: open objects サーバー構成オプション | Microsoft Docs
description: 無効になった "open objects" 構成オプションについて説明します。 開いているデータベース オブジェクトの数が SQL Server によってどのように管理されるようになったかを説明します。
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0bbcb11a80f06eae10e5481c965e9216cc84695e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773627"
---
# <a name="open-objects-server-configuration-option"></a>open objects サーバー構成オプション
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このオプションは引き続き **sp_configure** に存在しますが、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではその機能は無効になっています。 (設定しても効果はありません)。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、開いているデータベース オブジェクトの数が動的に管理され、使用できるメモリ量によってのみ制限されます。 **open objects** オプションは、既存スクリプトとの互換性のために **sp_configure** で使用できます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
