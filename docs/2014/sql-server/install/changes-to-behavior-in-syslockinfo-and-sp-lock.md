---
title: Syslockinfo および sp_lock の動作の変更 |Microsoft ドキュメント
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
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 982f31bbffb32726089fa331d105bfc262fc16a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075163"
---
# <a name="changes-to-behavior-in-syslockinfo-and-splock"></a>syslockinfo および sp_lock の動作に対する変更
  **syslockinfo**と**sp_lock**予期しない値を返す可能性があります。 可能性がありますを返すことも、追加の行が以前のバージョンの**syslockinfo**と**sp_lock**ロック リソースごとの 2 つの行の最大値が返されます。  
  
 情報にアクセスする**syslockinfo**実行または**sp_lock**サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 **Rsc_objid**と**rsc_indid**内の列**syslockinfo**と**objid**と**indid**内の列**sp_lock**一貫したオブジェクト ID を返すし、インデックスの id。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、値 0 が返される場合があります。  
  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 **Syslockinfo**と**sp_lock**単一のトランザクションで任意のロック リソースの 2 つの行の最大値を返します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、ロックのパーティション分割が有効である場合、1 つのトランザクションで実行している同じリソースに対して複数行が返されることがあります。 返される可能性が N + 1 行まで、N は Cpu の数。 さらに、同じリソースに対する GRANTED 要求および WAITING 要求を表示できます。[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、それらの要求を表示できませんでした。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
