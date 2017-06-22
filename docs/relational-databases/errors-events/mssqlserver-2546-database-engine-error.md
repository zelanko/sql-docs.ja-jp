---
title: MSSQLSERVER_2546 | Microsoft Docs
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
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 55278a84ecc717b9668af1b99bd2cf8ec3d5de16
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2546|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_INDEX_MARKED_DISABLED|  
|メッセージ テキスト|テーブル 'OBJECT_NAME' のインデックス 'INDEX_NAME' は無効に設定されています。 オンラインにするには、インデックスを再構築してください。|  
  
## <a name="explanation"></a>説明  
指定されているインデックスは、オフラインまたは無効に設定されています。 そのため、このインデックスをチェックできません。  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER INDEX を使用してインデックスを再構築します。  
  
## <a name="see-also"></a>参照  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[インデックスの再編成と再構築](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  

