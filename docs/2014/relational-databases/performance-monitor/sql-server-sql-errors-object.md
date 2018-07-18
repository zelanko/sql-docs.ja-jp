---
title: SQL Server:SQL Errors オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9d73add907b3ae4abd1250701b633e3cf1696217
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324242"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server:SQL Errors オブジェクト
  Microsoft **の** SQLServer:SQL Errors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトには、 **SQL Errors**を監視するカウンターが用意されています。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** のカウンターについて説明します。  
  
|SQL Server SQL Errors のカウンター|説明|  
|------------------------------------|-----------------|  
|**Errors/sec**|1 秒あたりのエラー数|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|アイテム|定義|  
|----------|----------------|  
|**_Total**|すべてのエラーに関する情報。|  
|**DB Offline Errors**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で現在のデータベースがオフラインになる原因となる重大なエラーを追跡します。|  
|**Info Errors**|問題を起こしているわけではない、ユーザーに情報提供を行っているエラーメッセージの情報。|  
|**Kill Connection Errors**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在の接続を強制的に切断する原因となる重大なエラーを追跡します。|  
|**User Errors**|ユーザー エラーに関する情報。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](monitor-resource-usage-system-monitor.md)  
  
  
