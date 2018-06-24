---
title: 互換性モードが 90 のテーブル ヒントを使用するときに、WITH キーワードを指定 |Microsoft ドキュメント
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
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: da01cc9f626f88c63a10da37540eb6fa00f1b0c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072477"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a>互換性モード 90 ではテーブル ヒントを使用するときに WITH キーワードを指定する
  例外がいくつかありますが、テーブル ヒントは WITH キーワードを使用して指定された場合のみクエリの FROM 句でサポートされます。 詳細については、[!INCLUDE[tsql](../../includes/tsql-md.md)] オンライン ブックの「FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])」および「テーブル ヒント ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])」を参照してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 テーブル ヒントの前に WITH キーワードを含めることによって、テーブル ヒントを FROM 句に含めてクエリを変更します。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
