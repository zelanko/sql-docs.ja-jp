---
title: WITH ROWS は、90以降の互換性モードの CREATE STATISTICS ステートメントではサポートされていません。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d28a05e7cd025e213e2cebdce9d582a9df446fea
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065046"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>互換性モード 90 以上では CREATE STATISTICS ステートメントで WITH ROWS がサポートされない
  互換性モードが 90 以上に設定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CREATE STATISTICS ステートメントに WITH ROWS を指定できません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 を使用する CREATE STATISTICS ステートメントを変更するには、WITH SAMPLE *number*行を指定するか、ドキュメント化された構文に準拠する他のオプションを指定します。 詳細については、「SQL Server オンラインブックでの CREATE STATISTICS (Transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
