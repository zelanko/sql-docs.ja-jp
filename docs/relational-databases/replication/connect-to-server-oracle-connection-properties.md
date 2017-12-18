---
title: "[サーバーへの接続](Oracle)、[接続プロパティ] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.oracleconnection.connectionprops.f1
helpviewer_keywords: Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 93059248f5787a812d22c30c915afe40a5ce2b86
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="connect-to-server-oracle-connection-properties"></a>[サーバーへの接続] (Oracle)、[接続プロパティ]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブを使用すると、**[ゲートウェイ]** または **[完全]** のパブリッシュ オプションを指定できます。 パブリッシャーを識別した後は、パブリッシャーをいったん削除して再構成しない限り、このオプションは変更できません。 詳細については、「[Configure an Oracle Publisher (Oracle パブリッシャーの構成)](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **[パブリッシャーの種類]**  
 **[ゲートウェイ]** または **[完全]**を選択します。 **[完全]** オプションを選択した場合は、Oracle パブリッシング用にサポートされる完全な機能セットがスナップショットおよびトランザクション パブリケーションに提供されます。 **[ゲートウェイ]** オプションを選択した場合は、レプリケーションがシステム間のゲートウェイとして動作する場合のパフォーマンスを向上させるために、特定のデザインが最適化されます。 複数のトランザクション パブリケーションに同じテーブルをパブリッシュする場合は、 **[ゲートウェイ]** オプションは使用できません。 **[ゲートウェイ]**オプションを選択した場合、1 つのテーブルは、最大で 1 つのトランザクション パブリケーションおよび任意の数のスナップショット パブリケーションに含めることができます。  
  
 **[タイムアウト]**  
 タイムアウト エラーが発生する前に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターが Oracle パブリッシャーへの接続を試みる期間を指定します。  
  
## <a name="see-also"></a>参照  
 [Oracle パブリッシングの用語](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Performance Tuning for Oracle Publishers](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
