---
title: バイナリ ラージ オブジェクト (Blob) を読み書きする UPDATETEXT ステートメントの変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cdfc74dddb01a064505e65e7d0aa67dd5b068739
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070402"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>バイナリ ラージ オブジェクト (BLOB) を読み書きする UPDATETEXT ステートメントを変更する
  アップグレード アドバイザーによって、同じバイナリ ラージ オブジェクト (BLOB) の読み取りおよび書き込みを実行する UPDATETEXT ステートメントが検出されました。このステートメントでは、同じテキスト ポインターが使用されています。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、このようなテキスト ポインターの使用方法はサポートされていません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 BLOB を一時テーブルまたはテーブル変数にコピーしてから、その値を元の列に割り当ててください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
