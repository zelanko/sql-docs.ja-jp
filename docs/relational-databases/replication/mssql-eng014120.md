---
title: MSSQL_ENG014120 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0f0ac589f95ddab413094239374c9c67b96c9e5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng014120"></a>MSSQL_ENG014120
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14120|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|ディストリビューション データベース '%s' を削除できませんでした。 このディストリビューション データベースはパブリッシャーに関連付けられています。|  
  
## <a name="explanation"></a>説明  
 ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションに対するトランザクションが格納されます。 このエラーは、1 つ以上のパブリッシャーに関連付けられているディストリビューション データベースを削除しようとした場合に発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 ディストリビューション データベースを削除するには、まずディストリビューターとパブリッシャーの関連付けを解除する必要があります。 詳細については、「[sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)  
  
  
