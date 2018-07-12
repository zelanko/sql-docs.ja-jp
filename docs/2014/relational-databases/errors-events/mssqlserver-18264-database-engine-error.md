---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4067cde7352144c9ade23999b85b7cdaf45d5f97
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420131"
---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|Microsoft SQL Server|  
|イベント ID|18264|  
|イベント ソース|MSSQLENGINE|  
|コンポーネント|SQLEngine|  
|シンボル名|STRMIO_DBDUMP|  
|メッセージ テキスト|データベースがバックアップされました。 データベース: %s、作成日 (時間): %s(%s)、ダンプされたページ: %d、最初の LSN: %s、最後の LSN: %s、ダンプ デバイスの数: %d、デバイス情報: (%s)。 このメッセージは情報提供だけを目的としています。 ユーザーによる操作は不要です。|  
  
## <a name="explanation"></a>説明  
 既定では、バックアップが成功するたびに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにこの情報メッセージが追加されます。 トランザクション ログを頻繁にバックアップすると、これらのメッセージがすぐに蓄積され、他のメッセージを探すのが困難になるほど大きなエラー ログが生成されることがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のトレース フラグ **3226** を使用すると、これらのログ エントリを除外できます。 頻度の高いログ バックアップを実行している場合やスクリプトがこれらのエントリに依存していない場合は、このトレース フラグを有効にすると便利です。  
  
 トレース フラグの使用方法の詳細については、SQL Server オンライン ブックを参照してください。  
  
## <a name="see-also"></a>参照  
 [トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
