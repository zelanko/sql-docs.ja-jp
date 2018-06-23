---
title: PH timeout サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
caps.latest.revision: 28
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f1e1caba1d80516359b5ef57f24a165e6d6d7598
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178529"
---
# <a name="ph-timeout-server-configuration-option"></a>PH timeout サーバー構成オプション
  PH timeout オプションは、フルテキスト プロトコル ハンドラーが、データベースへの接続をタイムアウトするまで待機する時間を秒単位で指定します。既定値は 60 秒です。 一時的なネットワークの問題により接続試行がタイムアウトする場合は、ph timeout 値を大きくします。  
  
 フルテキスト プロトコル ハンドラーは、フィルター デーモン ホストでホストされ、フルテキスト インデックスの作成対象データを SQL Server からフェッチする場合に使用されます。 フルテキスト検索コンポーネントの詳細については、「 [フルテキスト検索](../../relational-databases/search/full-text-search.md)」を参照してください。  
  
 データ行をフェッチすると、指定した時間内にプロトコル ハンドラーが SQL Server に接続できない場合、その行に対するタイムアウト エラーが報告されます。 その行のフェッチは、後でフルテキストの Gatherer により再試行されます。 フルテキストの Gatherer の詳細については、「 [フルテキスト インデックスの作成](../../relational-databases/indexes/indexes.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
