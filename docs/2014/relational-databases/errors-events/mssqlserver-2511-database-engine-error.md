---
title: MSSQLSERVER_2511 | Microsoft Docs
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
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9cfc320d29448dfa829e8741643d79df5c80061f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163868"
---
# <a name="mssqlserver2511"></a>MSSQLSERVER_2511
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2511|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_KEYS_OUT_OF_ORDER|  
|メッセージ テキスト|テーブル エラー: オブジェクト ID %d、インデックス ID %d、パーティション ID %I64d、アロケーション ユニット ID %I64d (型 %.*ls)。 ページ %S_PGID、スロット %d および %d のキーの順序が不正です。|  
  
## <a name="explanation"></a>説明  
 指定したインデックスで順序が不正なキーが検出されました。 キーを含むページが壊れている可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 ALTER INDEX REBUILD ステートメントを使用して、指定したインデックスを再構築します。  
  
  