---
title: SERVERPROPERTY は SQL Server 2005 | で LCID プロパティの正しい結果を返しますMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 24bb31759ba520f26b8e9af3a6533d8f0feebbe0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66092242"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>SQL Server 2005 では SERVERPROPERTY が LCID プロパティの正しい結果を返す
  SERVERPROPERTY('LCID') がバイナリ照合順序のサーバーで実行されると、この関数はサーバーの照合順序に対応した Windows ロケール識別子 (LCID) を返します。  
  
> [!NOTE]  
>  SERVERPROPERTY ('LCID') への参照を含むバッチ ファイルとトレース ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の他のインスタンスで実行される場合、他のインスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスと同じ照合順序である場合に限って、この動作変更があることが検出されます。  
  
## <a name="corrective-action"></a>修正措置  
 SERVERPROPERTY('LCID') がサーバーの照合順序に対応する Windows LCID を返すようにアプリケーションを修正してください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
