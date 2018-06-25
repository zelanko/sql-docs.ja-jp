---
title: 行を含むことはできません、互換性モード 90 以上で CREATE STATISTICS ステートメントで |Microsoft ドキュメント
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
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9d509352d99cab9359e7ea222f5fb2d5d7e28075
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163990"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>互換性モード 90 以上では CREATE STATISTICS ステートメントで WITH ROWS がサポートされない
  互換性モードが 90 以上に設定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CREATE STATISTICS ステートメントに WITH ROWS を指定できません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 サンプルを指定することで WITH ROWS を含む CREATE STATISTICS ステートメントを変更*数*行、または文書化されている構文に準拠するその他のオプションを指定することによってです。 詳細については、トピックの「CREATE STATISTICS (TRANSACT-SQL) で SQL Server オンライン ブックを参照してください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
