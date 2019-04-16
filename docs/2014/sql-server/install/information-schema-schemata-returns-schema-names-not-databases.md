---
title: INFORMATION_SCHEMA します。インスタンスでないデータベースのデータベースでは、スキーマを返しますスキーマ名 |。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c13ce7b709356e958d50271ea928f9b8464fb986
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582315"
---
# <a name="informationschemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA がインスタンスのデータベースではなく、データベースのスキーマ名を返す
  アップグレード アドバイザーによって、INFORMATION_SCHEMA.SCHEMATA ビューを参照するステートメントが検出されました。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このビューは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにあるすべてのデータベースを返しました。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、このビューはデータベース内のすべてのスキーマを返します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、INFORMATION_SCHEMA.SCHEMATA ビューは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにあるすべてのデータベースを返しました。 現在は、このビューは、SQL 標準に準拠した、データベースにあるすべてのスキーマを返します。  
  
## <a name="corrective-action"></a>修正措置  
 参照するアプリケーションの変更、 **sys.databases**カタログ ビューをインスタンス内のすべてのデータベースを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
