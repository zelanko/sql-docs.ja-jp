---
title: SQL Server:SQL Errors オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f36cd694756544a44df657d97fd84e1967167b55
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63183009"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server:SQL Errors オブジェクト
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**SQLServer: sql errors**オブジェクトには、 **SQL エラー**を監視するためのカウンターが用意されています。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** のカウンターについて説明します。  
  
|SQL Server SQL Errors のカウンター|[説明]|  
|------------------------------------|-----------------|  
|**1秒あたりのエラー数**|1 秒あたりのエラー数|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|アイテム|定義|  
|----------|----------------|  
|**_Total**|すべてのエラーに関する情報。|  
|**DB のオフラインエラー**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で現在のデータベースがオフラインになる原因となる重大なエラーを追跡します。|  
|**情報エラー**|問題を起こしているわけではない、ユーザーに情報提供を行っているエラーメッセージの情報。|  
|**強制終了接続エラー**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在の接続を強制的に切断する原因となる重大なエラーを追跡します。|  
|**ユーザーエラー**|ユーザー エラーに関する情報。|  
  
## <a name="see-also"></a>参照  
 [リソース使用状況の監視 &#40;システムモニタ&#41;](monitor-resource-usage-system-monitor.md)  
  
  
