---
title: Sysperfinfo.cntr_value から bigint 値を期待するアプリケーションの変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 303faa85853825b07eab52043929b92cbc601326
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249682"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntrvalue"></a>sysperfinfo.cntr_value から bigint 型の値を受け取れるようにアプリケーションを変更する
  sysperfinfo を返します、 `bigint` cntr_value 列の値。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 cntr_value 列の `bigint` 型の値を確実に処理できるように、sysperfinfo を使用するアプリケーションを変更してください。  
  
> [!NOTE]  
>  sysperfinfo は互換性ビューです。 代わりに、sys.dm_os_performance_counter 動的管理ビューを使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
