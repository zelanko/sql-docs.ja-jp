---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 757dabfc59775ac407dd5d1ceece2d067d32eacd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761600"
---
# <a name="mssqlserver9002"></a>MSSQLSERVER_9002
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9002|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LOG_IS_FULL|  
|メッセージ テキスト|データベース '%.*ls' のトランザクション ログがいっぱいです。 ログの領域を再利用できない理由を確認するには、sys.databases の log_reuse_wait_desc 列を参照してください。|  
  
## <a name="explanation"></a>説明  
データベース ログの容量不足です。 **sys.databases** の **log_reuse_wait_desc** 列に、ログの領域を再利用できない理由の説明があります。  
  
## <a name="user-action"></a>ユーザーの操作  
**sys.databases** を使用して、ログがいっぱいになった理由を調べ、その状況を解決します。 詳細については、SQL Server オンライン ブックの「満杯になったトランザクション ログのトラブルシューティング (エラー 9002)」を参照してください。  
  
## <a name="see-also"></a>参照  
[満杯になったトランザクション ログのトラブルシューティング &#40;SQL Server エラー 9002&#41;](~/relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
