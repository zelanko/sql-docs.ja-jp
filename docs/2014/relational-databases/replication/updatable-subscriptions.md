---
title: '[更新可能なサブスクリプション] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00d51c24583231f28ec15dd86c1848ba95c345d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255388"
---
# <a name="updatable-subscriptions"></a>[更新可能なサブスクリプション]
  トランザクションレプリケーションでは、レプリケートされたデータを読み取り専用として扱う必要があります。ただし、更新可能なサブスクリプションを使用し[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]て、サブスクライバーでレプリケートされたデータを変更することができます。 サブスクライバーでデータを変更する必要がある場合は、要件に応じて次のいずれかのオプションを選択してください。  
  
|更新可能なサブスクリプション タイプ|必要条件|  
|---------------------------------|------------------|  
|即時更新|サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続します。|  
|キュー更新|サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続する必要はありません。 更新をオフラインで実行し、後からパブリッシャーとサブスクライバーの間で同期させることができます。|  
  
## <a name="options"></a>オプション  
 **サブスクライバーの変更のレプリケート**  
 更新可能にする必要のある各サブスクライバーの **[レプリケート]** 列のチェック ボックスをオンにします。 これらの更新可能なサブスクライバーに対して、 **[パブリッシャーでのコミット]** 列のドロップダウン リスト ボックスから適切なオプションを選択します。  
  
-   即時更新サブスクリプションに対して **[変更を同時にコミットする]** を選択します。  
  
-   キュー更新サブスクリプションに対して **[変更をキューに登録し、可能な場合はコミット]** を選択します。  
  
## <a name="see-also"></a>参照  
 [プルサブスクリプションを作成する](create-a-pull-subscription.md)   
 [プッシュサブスクリプションを作成する](create-a-push-subscription.md)   
 [パブリケーションをサブスクライブする](subscribe-to-publications.md)   
 [トランザクションレプリケーションの更新可能なサブスクリプション](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
