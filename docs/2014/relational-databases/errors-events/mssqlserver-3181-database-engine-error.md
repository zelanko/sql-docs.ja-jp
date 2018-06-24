---
title: MSSQLSERVER_3181 | Microsoft Docs
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
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c2a5f0790969c43c3e8d55340ece141c7ab2069a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074827"
---
# <a name="mssqlserver3181"></a>MSSQLSERVER_3181
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|3181|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LDDB_STORAGE_VERIFY|  
|メッセージ テキスト|このバックアップの復元を試みるとストレージ領域に問題が発生する可能性があります。 詳細については、この後のメッセージを参照してください。|  
  
## <a name="explanation"></a>説明  
 RESTORE VERIFYONLY ステートメントでは、データベースの復元先ディスクの利用可能なストレージ領域がチェックされます。  
  
### <a name="possible-causes"></a>考えられる原因  
 使用可能なディスク領域が不十分なため、確認中のバックアップを復元できない可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 十分なディスク領域があるドライブにバックアップを復元するか、ディスク領域を増やします。  
  
## <a name="see-also"></a>参照  
 [データベースを新しい場所に復元する &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [ファイルを新しい場所に復元&#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
