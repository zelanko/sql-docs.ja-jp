---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26a6a753942bfb111a5e2b5c6b821577d660cc12
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656750"
---
# <a name="mssqlserver2511"></a>MSSQLSERVER_2511
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
