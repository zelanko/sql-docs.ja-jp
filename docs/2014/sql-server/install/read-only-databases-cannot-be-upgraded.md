---
title: 読み取り専用データベースをアップグレードすることはできません |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 11f94ceed205d8984ed5a253e1d989211012f10f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179059"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>読み取り専用データベースをアップグレードできない
  アップグレード アドバイザーによって、この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにある一部のデータベースをアップグレードできないことが判定されました。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 読み取り専用データベースが検出されました。 データベースをアップグレードするには、セットアップ時にそのデータベースへの書き込みが可能である必要があります。  
  
## <a name="corrective-action"></a>修正措置  
 誰が使用すると、データベースを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、または、ALTER DATABASE ステートメントを読み取り/書き込みデータベースを変更します。 次のステートメントを使用すると、データベースが読み取り/書き込み可能に変更されます。  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 ALTER DATABASE ステートメントの詳細については、[!INCLUDE[tsql](../../includes/tsql-md.md)] オンライン ブックのトピック「ALTER DATABASE ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
