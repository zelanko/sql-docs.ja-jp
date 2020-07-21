---
title: Sysperfinfo から bigint 値を期待するようにアプリケーションを変更します。 cntr_value |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 108a9b981debc95e182b16847c39a03d4b242088
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012206"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a>sysperfinfo.cntr_value から bigint 型の値を受け取れるようにアプリケーションを変更する
  sysperfinfo は `bigint` 、cntr_value 列の値を返します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 cntr_value 列の `bigint` 型の値を確実に処理できるように、sysperfinfo を使用するアプリケーションを変更してください。  
  
> [!NOTE]  
>  sysperfinfo は互換性ビューです。 代わりに、sys.dm_os_performance_counter 動的管理ビューを使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
