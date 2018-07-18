---
title: SQL Server 2005 で SERVERPROPERTY が LCID プロパティの正確な結果を返します |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9a92dd33ee5693d78b5f55f3bfcbc6edb4a0d8b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157703"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>SQL Server 2005 では SERVERPROPERTY が LCID プロパティの正しい結果を返す
  SERVERPROPERTY('LCID') がバイナリ照合順序のサーバーで実行されると、この関数はサーバーの照合順序に対応した Windows ロケール識別子 (LCID) を返します。  
  
> [!NOTE]  
>  SERVERPROPERTY ('LCID') への参照を含むバッチ ファイルとトレース ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の他のインスタンスで実行される場合、他のインスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスと同じ照合順序である場合に限って、この動作変更があることが検出されます。  
  
## <a name="corrective-action"></a>修正措置  
 SERVERPROPERTY('LCID') がサーバーの照合順序に対応する Windows LCID を返すようにアプリケーションを修正してください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
