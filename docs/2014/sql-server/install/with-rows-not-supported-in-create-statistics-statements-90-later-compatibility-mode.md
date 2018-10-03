---
title: WITH ROWS は互換モードが 90 以上で CREATE STATISTICS ステートメントではサポートされませんが |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7318340d5bf5e5861c1a95d6fa8cc9e54679f4a5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137512"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>互換性モード 90 以上では CREATE STATISTICS ステートメントで WITH ROWS がサポートされない
  互換性モードが 90 以上に設定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CREATE STATISTICS ステートメントに WITH ROWS を指定できません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 サンプルを指定することで WITH ROWS を含む CREATE STATISTICS ステートメントを変更*数*行、または文書化されている構文に準拠するその他のオプションを指定することで。 詳細については、「CREATE STATISTICS (TRANSACT-SQL) で SQL Server オンライン ブック トピックを参照してください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
