---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7ba3d6abdd1f25b9fef9543e8a9a04dd2158261c
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1458|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBM_FAILREDO_ON_PRIMARY|  
|メッセージ テキスト|'%.*ls' データベースのプリンシパル コピーでエラー %d、ステータス %d、重要度 %d が発生しました。 データベース ミラーリングは中断されました。 エラー状態を解決して、ミラーリングを再開してください。|  
  
## <a name="explanation"></a>説明  
このメッセージは、データベース ミラーリングを中断させるエラーがプリンシパル データベースで検出されたことを示しています。  
  
## <a name="user-action"></a>ユーザーの操作  
このエラーはほとんどの場合、自動で修復されます。 問題が修正されない場合、通常はデータベースまたはサーバー インスタンスを再起動することで問題が解決されます。 詳細については、各パートナーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを参照し、このメッセージに先行する関連エラーがないかどうかを確認してください。  
  
## <a name="see-also"></a>参照  
[データベース ミラーリングの監視 &#40;SQL Server&#41;](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  

