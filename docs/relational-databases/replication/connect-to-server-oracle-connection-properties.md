---
title: "[サーバーへの接続] (Oracle)、[接続プロパティ] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.oracleconnection.connectionprops.f1"
helpviewer_keywords: 
  - "[サーバーへの接続] ダイアログ ボックス, レプリケーション"
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# [サーバーへの接続] (Oracle)、[接続プロパティ]
  使用して、 **接続プロパティ** のタブ、 **サーバーへの接続** の公開オプションを指定する] ダイアログ ボックス **ゲートウェイ** または **完了**します。 パブリッシャーを識別した後は、パブリッシャーをいったん削除して再構成しない限り、このオプションは変更できません。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
## オプション  
 **[パブリッシャーの種類]**  
 選択 **ゲートウェイ** または **完了**します。 **[完全]** オプションを選択した場合は、Oracle パブリッシング用にサポートされる完全な機能セットがスナップショットおよびトランザクション パブリケーションに提供されます。 **[ゲートウェイ]** オプションを選択した場合は、レプリケーションがシステム間のゲートウェイとして動作する場合のパフォーマンスを向上させるために、特定のデザインが最適化されます。 複数のトランザクション パブリケーションに同じテーブルをパブリッシュする場合は、 **[ゲートウェイ]** オプションは使用できません。 **[ゲートウェイ]**オプションを選択した場合、1 つのテーブルは、最大で 1 つのトランザクション パブリケーションおよび任意の数のスナップショット パブリケーションに含めることができます。  
  
 **[タイムアウト]**  
 指定期間、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターをするべきでタイムアウト エラーが発生する前に、Oracle パブリッシャーに接続します。  
  
## 参照  
 [Oracle パブリッシングの用語](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Oracle パブリッシャーのパフォーマンス チューニング](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  