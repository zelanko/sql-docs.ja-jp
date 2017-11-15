---
title: MSSQL_ENG020596 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a0260be11a86a4f311d45e8f69e206af0985048
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng020596"></a>MSSQL_ENG020596
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|20596|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|'%s' または db_owner のメンバーだけが匿名エージェントを削除できます。|  
  
## <a name="explanation"></a>説明  
 匿名サブスクリプションのエージェントを削除するために必要な権限がありません。 [sp_dropanonymousagent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) を呼び出すときに使用するログインは、ディストリビューターの固定サーバー ロール **sysadmin** またはディストリビューション データベースの固定データベース ロール **db_owner** のメンバーであるか、エージェントを最初に起動したユーザーである必要があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 適切な資格情報でログインして **sp_dropanonymousagent**を実行します。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
