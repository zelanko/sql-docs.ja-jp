---
title: '[サーバーへの接続] (Oracle)、[接続プロパティ] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f675a41138121a017096c1025698d34529468f49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180092"
---
# <a name="connect-to-server-oracle-connection-properties"></a>[サーバーへの接続] \(Oracle)、[接続プロパティ]
  **[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブを使用すると、 **[ゲートウェイ]** または **[完全]** のパブリッシュ オプションを指定できます。 パブリッシャーを識別した後は、パブリッシャーをいったん削除して再構成しない限り、このオプションは変更できません。 詳細については、「[Configure an Oracle Publisher (Oracle パブリッシャーの構成)](non-sql/configure-an-oracle-publisher.md)」をご覧ください。  
  
## <a name="options"></a>および  
 **[パブリッシャーの種類]**  
 **[ゲートウェイ]** または **[完全]** を選択します。 **[完全]** オプションを選択した場合は、Oracle パブリッシング用にサポートされる完全な機能セットがスナップショットおよびトランザクション パブリケーションに提供されます。 **[ゲートウェイ]** オプションを選択した場合は、レプリケーションがシステム間のゲートウェイとして動作する場合のパフォーマンスを向上させるために、特定のデザインが最適化されます。 複数のトランザクション パブリケーションに同じテーブルをパブリッシュする場合は、 **[ゲートウェイ]** オプションは使用できません。 **[ゲートウェイ]** オプションを選択した場合、1 つのテーブルは、最大で 1 つのトランザクション パブリケーションおよび任意の数のスナップショット パブリケーションに含めることができます。  
  
 **[タイムアウト]**  
 タイムアウト エラーが発生する前に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターが Oracle パブリッシャーへの接続を試みる期間を指定します。  
  
## <a name="see-also"></a>参照  
 [Glossary of Terms for Oracle Publishing (Oracle パブリッシングの用語)](non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Performance Tuning for Oracle Publishers](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
