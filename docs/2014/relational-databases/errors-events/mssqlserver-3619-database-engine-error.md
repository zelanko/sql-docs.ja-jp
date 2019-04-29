---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6a82902d69a1d5214b29f43d19ded58c76293ec4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914028"
---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
