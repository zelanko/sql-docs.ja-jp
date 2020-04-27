---
title: INFORMATION_SCHEMA。スキーマは、インスタンス内のデータベースではなく、データベース内のスキーマ名を返します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e3683ee043785ec6adc349ac52301280c7bc2b8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094728"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA がインスタンスのデータベースではなく、データベースのスキーマ名を返す
  アップグレード アドバイザーによって、INFORMATION_SCHEMA.SCHEMATA ビューを参照するステートメントが検出されました。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このビューは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにあるすべてのデータベースを返しました。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、このビューはデータベース内のすべてのスキーマを返します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、INFORMATION_SCHEMA.SCHEMATA ビューは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにあるすべてのデータベースを返しました。 現在は、このビューは、SQL 標準に準拠した、データベースにあるすべてのスキーマを返します。  
  
## <a name="corrective-action"></a>修正措置  
 のインスタンス内のすべての**sys.databases** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを返すように、アプリケーションを変更して、データベースカタログビューを参照します。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
