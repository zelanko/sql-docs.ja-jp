---
title: "[パブリケーションのプロパティ]、[全般] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.general.f1
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bb22c4211fcf7d5e07f2105f221495cbadd8d9c6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="publication-properties-general"></a>[パブリケーションのプロパティ]、[全般]
  **[パブリケーションのプロパティ]** ダイアログ ボックスの **[全般]** ページには、名前、説明、およびサブスクリプションの有効期限ポリシーなどの、パブリケーションに関する基本情報が表示されます。  
  
## <a name="options"></a>オプション  
 **名前**  
 パブリケーションの名前です (読み取り専用)。  
  
 **データベース**  
 パブリケーション データベースの名前です (読み取り専用)。  
  
 **説明**  
 パブリケーションの説明です。  
  
 **型**  
 パブリケーションの種類です (読み取り専用)。  
  
 **[サブスクリプションの有効期限]**  
 サブスクリプションの有効期限として、 **[サブスクリプションの有効期限はありません]** または **[次の間隔で同期していないサブスクリプションは有効期限が切れ、削除される可能性があります]**を選択します。後者を選択した場合は、明示的な期間 (**[間隔]**) を設定します。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、スナップショット パブリケーションおよびトランザクション パブリケーションに対しては、 **[サブスクリプションの有効期限はありません]**の既定値を使用することをお勧めします。  
  
 マージ レプリケーションに対しては、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、 **[次の間隔で同期していないサブスクリプションは有効期限が切れ、削除される可能性があります]** の既定値を使用し、 **[間隔]**にできる限り小さい値を設定することをお勧めします。 サブスクリプションの有効期限が長くなると、格納されるメタデータの量が増え、パフォーマンスに影響が及ぶ可能性があります。 サブスクライバーを切断したり期間を延長して同期化したりするだけでなく、大量のメタデータの格納および処理に伴うパフォーマンス上の問題とのバランスを考慮してください。  
  
 詳細については、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
 **互換性レベル**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only; merge publications only. このパブリケーションと同期するサブスクライバーに必要な最低限の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンを選択します。 互換性レベルの決定に関してはいくつかのルールがあります。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
