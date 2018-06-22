---
title: MSSQLSERVER_17132 | Microsoft Docs
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
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8a23c91789ee0d2795f820e7edf5d16936aa2299
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076879"
---
# <a name="mssqlserver17132"></a>MSSQLSERVER_17132
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17132|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|INIT_NODESSPACE|  
|メッセージ テキスト|記述子用のメモリが不足しているので、サーバーのスタートアップに失敗しました。 不要なメモリ負荷を減らすか、システム メモリを増やしてください。|  
  
## <a name="explanation"></a>説明  
 サーバー内部の記述子を格納するための十分なメモリの割り当てに失敗しました。  
  
## <a name="user-action"></a>ユーザーの操作  
 コンピューターにメモリを追加してください。 一般的なメモリのトラブルシューティング手順を使用できます。  
  
  