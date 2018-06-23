---
title: OPENXML の XPath 式をサポートされていない関数を削除する更新 |Microsoft ドキュメント
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
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 768124887a7d75797229919d7d7399df9ce4b130
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164218"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a>OPENXML XPath 式の更新によりサポートされていない関数が削除される
  アップグレード アドバイザーによって、XPath 機能の使用が検出されました。 OPENXML の XPath 機能が変更されているので、アップグレードした後でその影響を受ける可能性があります。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 現在では、MSXML 3.0 が、OPENXML クエリ内で使用される XPath 式を処理するための基本エンジンとなっています。 MSXML 3.0 には、より精密な XPath 1.0 エンジンがあります。これにより、以下の関数のサポートが削除されています。  
  
-   format-number()  
  
-   formatNumber()  
  
-   current()  
  
-   element-available()  
  
-   function-available()  
  
-   system-property()  
  
## <a name="corrective-action"></a>修正措置  
 format-number() と formatNumber() の場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用できます。 前述したその他のサポートされていない関数については、直接的な対応策はありません。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
