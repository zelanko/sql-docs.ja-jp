---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 16f0a8de9e55759e78c8fd2cd136ff4db3a677a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62734984"
---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
