---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 963267a102c16b57860d5859a6600a34781ca2c8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413801"
---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3619|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SYS_NOLOG|  
|メッセージ テキスト|ログに空き領域がないので、データベース ID %d にチェックポイント レコードを書き込めませんでした。 データベース管理者に問い合わせて、ログを切り捨てるか、データベース ログ ファイルに追加領域を割り当ててください。|  
  
## <a name="explanation"></a>説明  
 トランザクション ログ用のディスク容量が不足しています。  
  
## <a name="user-action"></a>ユーザーの操作  
 ログの切り捨てを行って容量を解放するか、ログ ファイルに追加領域を割り当てます。 詳細については、SQL Server オンライン ブックの「満杯になったトランザクション ログのトラブルシューティング (エラー 9002)」を参照してください。  
  
  
