---
title: MSSQL_ENG003724 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7075db02099e3797031f3ecafd7465644a2db795
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="mssqleng003724"></a>MSSQL_ENG003724
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3724|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|%S_MSG '%.*ls' を %S_MSG できません。レプリケーションに使用されています。|  
  
## <a name="explanation"></a>説明  
 データベース内のオブジェクトがレプリケートされると、システム テーブル **sysarticles** (スナップショット パブリケーションまたはトランザクション パブリケーションの場合) または **sysmergearticles** (マージ パブリケーションの場合) に、レプリケート済みのマークが付けられています。 レプリケート済みのオブジェクトを削除しようとした場合に、このエラーが発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 データベース オブジェクトを削除する前に、そのオブジェクトがレプリケートされていないことを確認します。 例:  
  
-   パブリケーション データベースでエラーが発生した場合、オブジェクトを削除する前にパブリケーションからアーティクルを削除します。 詳細については、「[既存のパブリケーションでのアーティクルの追加および削除](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。  
  
-   サブスクリプション データベースでエラーが発生した場合、オブジェクトを削除する前にそのサブスクリプションを削除します。 詳細については、「[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)」を参照してください。 トランザクション パブリケーションに対するサブスクリプションの場合、パブリケーション全体を削除するのではなく、個々のアーティクルに対するサブスクリプションを削除することができます。 詳細については、「[sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)」を参照してください。  
  
 レプリケートされていないデータベースでこのエラーが発生した場合は、[sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) を実行して、データベース内のオブジェクトにレプリケート済みのマークが付かないようにしてください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
