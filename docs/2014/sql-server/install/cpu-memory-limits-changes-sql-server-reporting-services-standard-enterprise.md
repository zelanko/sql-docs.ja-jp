---
title: SQL Server Reporting Services Standard および Enterprise CPU とメモリの制限に変更点 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: efc71378e6570a86d075ed50e206284a93b0532a
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353869"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>SQL Server Reporting Services Standard および Enterprise での CPU およびメモリの制限の変更点
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services Standard Edition および Enterprise Edition では、最大 64 GB のシステム メモリがサポートされています。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Reporting Services Standard Edition および Enterprise Edition では、最大 64 GB のシステム メモリがサポートされています。 必要に応じて、新しい制限に合うように現在のシステム設定を再構成してください。  
  
 その他のエディションの CPU とメモリの制限の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[Compute Capacity Limits by Edition の SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md)、および[メモリは、SQL Server の各エディションでサポートされている](https://go.microsoft.com/fwlink/?LinkId=212633)します。  
  
## <a name="corrective-action"></a>修正措置  
 必要に応じて、新しい CPU およびメモリの制限に合うように現在のシステム設定を再構成してください。 詳細については、次を参照してください。 [ALTER SERVER CONFIGURATION &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)、および[サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のエディションでサポートされる機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [旧バージョンとの互換性](../../../2014/getting-started/backward-compatibility.md)  
  
  
