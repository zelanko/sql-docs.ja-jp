---
title: バイナリラージオブジェクト (Blob) の読み取りと書き込みを行う UPDATETEXT ステートメントを変更します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 061e7bad0bae5a74d103406265ad79195f79f7db
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059211"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>バイナリ ラージ オブジェクト (BLOB) を読み書きする UPDATETEXT ステートメントを変更する
  アップグレード アドバイザーによって、同じバイナリ ラージ オブジェクト (BLOB) の読み取りおよび書き込みを実行する UPDATETEXT ステートメントが検出されました。このステートメントでは、同じテキスト ポインターが使用されています。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、このようなテキスト ポインターの使用方法はサポートされていません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 BLOB を一時テーブルまたはテーブル変数にコピーしてから、その値を元の列に割り当ててください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
