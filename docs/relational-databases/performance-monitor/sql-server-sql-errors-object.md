---
title: SQL Server:SQL Errors オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: b8f99ab36545778981ed509ed0575c039916d42f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758935"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server:SQL Errors オブジェクト
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **SQLServer:SQL Errors** オブジェクトには、 **SQL Errors**を監視するカウンターが用意されています。  
  
 次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** カウンターについて説明します。  
  
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
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
