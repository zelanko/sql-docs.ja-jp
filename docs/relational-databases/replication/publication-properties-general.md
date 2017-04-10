---
title: "[パブリケーションのプロパティ]、[全般] | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.general.f1"
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# [パブリケーションのプロパティ]、[全般]
   **全般** のページ、 **パブリケーションのプロパティ** ] ダイアログ ボックスには、名前、説明、およびサブスクリプションの有効期限ポリシーを含めて、パブリケーションに関する基本的な情報が含まれています。  
  
## オプション  
 **名前**  
 パブリケーションの名前です (読み取り専用)。  
  
 **データベース**  
 パブリケーション データベースの名前です (読み取り専用)。  
  
 **説明**  
 パブリケーションの説明です。  
  
 **型**  
 パブリケーションの種類です (読み取り専用)。  
  
 **[サブスクリプションの有効期限]**  
 サブスクリプションの有効期限のオプションのいずれかを選択: **サブスクリプションの有効期限なし** または **サブスクリプションの有効期限**, 、明示的な期間に (**間隔**)。  
  
 スナップショット レプリケーションおよびトランザクション パブリケーション、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] の既定設定を受け入れることをお勧め **サブスクリプションの有効期限なし**します。  
  
 マージ レプリケーションで [!INCLUDE[msCoName](../../includes/msconame-md.md)] の既定設定を受け入れることをお勧め **サブスクリプションの有効期限** では、できるだけ小さい値を設定および **間隔**します。 サブスクリプションの有効期限が長くなると、格納されるメタデータの量が増え、パフォーマンスに影響が及ぶ可能性があります。 サブスクライバーを切断したり期間を延長して同期化したりするだけでなく、大量のメタデータの格納および処理に伴うパフォーマンス上の問題とのバランスを考慮してください。  
  
 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
 **互換性レベル**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンだけです。マージ パブリケーションのみです。 このパブリケーションと同期するサブスクライバーに必要な最低限の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンを選択します。 互換性レベルの決定に関してはいくつかのルールがあります。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  