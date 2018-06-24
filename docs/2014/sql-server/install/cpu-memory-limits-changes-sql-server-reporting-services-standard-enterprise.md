---
title: SQL Server Reporting Services Standard および Enterprise の CPU およびメモリの制限に変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5097398d50c2e3072c31724cd16e56d63f5e7676
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072055"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>SQL Server Reporting Services Standard および Enterprise での CPU およびメモリの制限の変更点
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services Standard Edition および Enterprise Edition では、最大 64 GB のシステム メモリがサポートされています。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Reporting Services Standard Edition および Enterprise Edition では、最大 64 GB のシステム メモリがサポートされています。 必要に応じて、新しい制限に合うように現在のシステム設定を再構成してください。  
  
 他のエディションの CPU とメモリの制限の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md)、および[SQL Server の各エディションがサポートするメモリ](http://go.microsoft.com/fwlink/?LinkId=212633)です。  
  
## <a name="corrective-action"></a>修正措置  
 必要に応じて、新しい CPU およびメモリの制限に合うように現在のシステム設定を再構成してください。 詳細については、次を参照してください。 [ALTER SERVER CONFIGURATION &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)、および[サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションでサポートされる機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [旧バージョンとの互換性](../../../2014/getting-started/backward-compatibility.md)  
  
  
