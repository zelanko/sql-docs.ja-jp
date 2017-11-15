---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 870b2060d5a43e3e8cfd3430e38ef95356d492ef
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver7711"></a>MSSQLSERVER_7711
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7711|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PRT_RANGE_OVERLAP|  
|メッセージ テキスト|テーブル、インデックス、またはパーティションの 1 つに DATA_COMPRESSION オプションが複数回指定されました。|  
  
## <a name="explanation"></a>説明  
次のステートメントのいずれかの DATA_COMPRESSION オプションでエラーが発生しました。  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
引用されたテーブルまたはインデックスがパーティション分割されている場合、少なくとも 1 つのパーティションで DATA_COMPRESSION オプションが 2 回以上指定されました。 テーブルまたはインデックスがパーティション分割されていない場合、DATA_COMPRESSION オプションが 2 回以上引用されました。  
  
## <a name="user-action"></a>ユーザーの操作  
パーティション分割されたテーブルまたはインデックスの場合、各パーティションに DATA_COMPRESSION オプションを 1 回だけ指定するようにしてください。 パーティション分割されていないテーブルまたはインデックスの場合、ステートメントに DATA_COMPRESSION オプションを 1 回だけ使用してください。  
  
