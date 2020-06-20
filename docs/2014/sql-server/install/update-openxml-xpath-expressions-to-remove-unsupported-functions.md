---
title: サポートされていない関数を削除するように OPENXML XPath 式を更新する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041772"
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
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
