---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4cf38de44578c382d30ed1854bda7f25b83b4020
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410971"
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
  
  
