---
title: バイナリ ラージ オブジェクト (Blob) を読み書きする UPDATETEXT ステートメントを変更 |Microsoft ドキュメント
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
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5b0c6df5c9324a35f1f642d366ef8f2780341592
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173630"
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
  
  
