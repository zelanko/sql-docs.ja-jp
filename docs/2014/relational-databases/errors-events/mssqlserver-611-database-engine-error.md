---
title: MSSQLSERVER_611 | Microsoft Docs
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
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fc1a8b3bc8f492e73b543ce7551dfba52a1dbd55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071877"
---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|611|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|VAR_SIZE_TOO_BIG|  
|メッセージ テキスト|行を挿入または更新できません。オーバーヘッドを含む、変数列の合計サイズが、制限を超える %d バイトです。|  
  
## <a name="explanation"></a>説明  
 最大の可変長の列サイズがスキーマで許可されている値を超えています。 vardecimal ストレージ形式を設定したときに可変長の列が固定値の制限を超えているか、可変長の列サイズが圧縮データ レコードの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で許可されている制限を超えていた場合に、エラー 611 が返されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 レコードのサイズを縮小します。  
  
  