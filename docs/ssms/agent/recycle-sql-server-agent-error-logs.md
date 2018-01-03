---
title: "[SQL Server エージェント エラー ログの再利用] | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 349ae61e3ed53912f2f25565f9db7a99f4b56b56
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="recycle-sql-server-agent-error-logs"></a>[SQL Server エージェント エラー ログの再利用]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント エラー ログを再利用できます。 ログを再利用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを再起動しなくても、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント エラー ログが閉じ、新しいエラー ログが開始します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントで保持されるエラー ログは直前の 9 個までであることに注意してください。 既にエラー ログが 9 個に達している場合は、エラー ログを再利用すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは最も古いエラーログを削除します。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェント エラー ログ](../../ssms/agent/sql-server-agent-error-log.md)  
  
